# monorepo 環境構築

1. project の作成

```shell
pnpm init
```

2. workspace として使用するための設定

### `package.json`

```json
{
  ...
  "engines": {
  "pnpm": "9.2.0"
  },
  "packageManager": "pnpm@9.2.0"
 ...
}
```

### `pnpm-workspace.yaml`

```yaml
packages:
  #include
  - "packages/*"
  #exclude
  - "!exclude_dir/**"
```

3. サブパッケージの scripts を実行する

```json
{
 ...
 "scripts": {
   "[package名]": "pnpm -F \"[ディレクトリ名]\"",
 },
 ...
}
```

実行コマンド

```shell
pnpm [package名] [コマンド]
```

4. サブパッケージに対して`pnpm`に関する操作を行う

```shell
pnpm [pkg名] [コマンド]
```

ex) サプパッケージに依存 package を入れる

```shell
pnpm [pkg名] add -E ""
```

※`-E`または`--save-exact`はバージョンをあるバージョンに固定できる

ex) サブパッケージのテストを実行

```shell
pnpm [pkg名] test
```

## 参考サイト

https://zenn.dev/wakamsha/articles/construct-monorepo-with-pnpm

https://qiita.com/macropygia/items/7d9a06cf33ec4997dcfa
