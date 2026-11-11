# writing

記事を取得するには、リポジトリ直下で次を実行する。

```sh
blogsync pull shibayu36.hatenablog.com
```

`mise.toml` の `[shell_alias]` で、このリポジトリ内では `blogsync` が `op run --env-file=blogsync.env -- blogsync` になる。初回は `mise trust` が必要。
