# packer_shell_env_test

Packer でローカルの環境変数を渡す方法を試してみたのでメモしておく。

## 事前準備

AWSのAMIを焼くので、コンソールにアクセスキーとシークレットキーを設定しておく

- AWS CLI のプロファイル設定 (`[default]` 設定)
- `AWS_ACCESS_KEY_ID` および `AWS_SECRET_ACCESS_KEY` 環境変数の設定

## 環境変数を設定

試験用の環境変数をローカルで設定しておく

```shell
$ export TEST="It's a test!"
```

## Packer Build 実行

`-var-file` で variables.json を読み込む。

```shell
$ packer build -var-file=variables.json test-ami.json
```

実行すると、ログにローカルの `TEST` 環境変数の値が表示される。

以上。


# 参考

- https://www.packer.io/docs/templates/user-variables.html
- https://www.packer.io/docs/provisioners/shell.html