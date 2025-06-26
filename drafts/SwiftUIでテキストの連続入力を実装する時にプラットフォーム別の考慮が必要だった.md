SwiftUIでテキストの連続入力を実装したいと思ったが、プラットフォームごとで異なる問題にハマった。iOSではonSubmitを使うとソフトウェアキーボードが一瞬閉じてしまい、macOSではonChangeだけだとEnterキーでの改行入力が反映されない。

### 背景・やりたかったこと

アプリで項目を連続して入力できる機能を作りたかった。具体的には、テキストフィールドでEnterキーを押したら項目が追加され、すぐに次の項目を入力できる状態になってほしい。こういう流れだ。

1. テキストフィールドに「項目1」と入力
2. Enterキーを押す
3. 「項目1」がリストに追加される
4. テキストフィールドがクリアされて、フォーカスは残ったまま
5. 続けて「項目2」を入力できる

一見簡単そうに見えるが、実装してみるとプラットフォームごとに異なる問題が発生した。

### 実装してみた

最初は一般的なonSubmitを使った実装を試してみた。

```swift
TextField("新しいアイテムを追加", text: $inputText, axis: .vertical)
    .focused($isInputFocused)
    .onSubmit {
        addItem()
    }
```

この実装では、Enterキーを押すとaddItem()が呼ばれ、テキストをクリアしてisInputFocusedを保持したままにすることで連続入力を実現しようとした。

macOSでは期待通りに動作した。しかし、iOSで試してみると問題が発生した。

### ハマったポイント

#### iOSでソフトウェアキーボードが一瞬閉じる

iOSでonSubmitを使うと、Enterキーを押した瞬間にソフトウェアキーボードが一瞬閉じてしまう。その後すぐに開き直すのだが、この一瞬のちらつきがユーザー体験を大きく損なう。

原因を調べてみると、onSubmitはもともと「入力完了」を意味するイベントのため、システム側がキーボードを閉じようとするらしい。@FocusStateでフォーカスを保持していても、この瞬間的なキーボードの開閉は避けられなかった。

そこで、iOSではonChangeで改行文字を検知する方法に変更した。

```swift
.onChange(of: inputText) { _, newValue in
    guard isInputFocused else { return }
    guard newValue.contains("\n") else { return }
    addItem()
}
```

これでiOSのキーボード問題は解決した。

#### macOSでonChangeだとEnterキーが効かない  

一方で、macOSでonChangeのみを使うと別の問題が発生した。Enterキーを押しても何も起こらないのだ。

詳しく調べてみると、macOSのTextFieldでは改行文字（\n）は入力されないことが分かった。macOSのTextFieldはデスクトップアプリケーションの一般的な動作に合わせて、Enterキーを「入力確定」として扱うため、改行文字として認識されない。

そのため、macOSではonSubmitを使う必要がある。

### 解決策: プラットフォーム分岐

結果的に、プラットフォームごとに異なるアプローチを使い分けることになった。

```swift
import SwiftUI

struct ContentView: View {
  @State private var inputText = ""
  @State private var items: [String] = []
  @FocusState private var isInputFocused: Bool

  var body: some View {
    VStack {
      ForEach(items, id: \.self) { item in
        Text(item)
      }

      // axis: .verticalで複数行入力に対応
      TextField("新しいアイテムを追加", text: $inputText, axis: .vertical)
        // 追加時にisInputFocusedの状態を変えないので、入力し続けられる
        .focused($isInputFocused)
        #if os(iOS)
          // iOS: onChangeで改行文字を検知して追加処理を実行
          // onSubmitを使うとキーボードが一瞬閉じてしまう
          .onChange(of: inputText) { _, newValue in
            guard isInputFocused else { return }

            // 改行文字(\n)が含まれているなら追加処理を実行
            guard newValue.contains("\n") else { return }
            addItem()
          }
        #else
          // macOSなどiOS以外: 通常通りonSubmitでEnterキー押下を検知
          // macOSでonChangeを使うとEnterキーで追加できなくなる
          .onSubmit {
            addItem()
          }
        #endif
    }
  }

  private func addItem() {
    let trimmedText = inputText.trimmingCharacters(in: .whitespacesAndNewlines)
    guard !trimmedText.isEmpty else { return }

    items.append(trimmedText)
    inputText = ""
  }
}
```

ポイントは以下の通り：

- **iOS**: `onChange`で改行文字を検知してアイテム追加
- **macOS等**: `onSubmit`でEnterキー押下を検知してアイテム追加
- `@FocusState`でフォーカス状態を管理し、アイテム追加後もフォーカスを保持
- `axis: .vertical`で複数行入力に対応
- `trimmingCharacters`で余分な空白や改行を削除

### まとめ

SwiftUIでテキストの連続入力を実装する際は、プラットフォームごとの動作の違いを考慮する必要があると分かった。

- iOSではonSubmitを使うとキーボードのちらつき問題がある
- macOSではonChangeだけだとEnterキーの無効化問題がある

今回のようにプラットフォーム分岐を使うことで、どちらの環境でも期待通りの動作を実現できた。

ただし、この実装だとvisionOSなど新しいプラットフォームが追加された時の動作が分からない。また、SwiftUI自体のアップデートでより良い解決策が提供される可能性もある。他に良いやり方があれば募集。