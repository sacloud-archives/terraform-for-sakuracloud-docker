> :warning: Terraform for さくらのクラウドのDockerHubでのDockerイメージ配布は廃止されました。  

# Terraform for さくらのクラウド

[Terraform for さくらのクラウド](https://github.com/sacloud/terraform-provider-sakuracloud)用Dockerイメージ

**0.6.2以降、WORKDIRが`/workdir`へ変更されました**

## 使い方(dockerコマンドを直接使う場合)

### 起動コマンド書式

```bash
docker run -it --rm sacloud/terraform 実行したいコマンド
```

### `terraform plan`実行例
```bash
docker run -it --rm -e SAKURACLOUD_ACCESS_TOKEN -e SAKURACLOUD_ACCESS_TOKEN_SECRET -v $PWD:/workdir sacloud/terraform plan
```

## 使い方(whalebrewを使う場合)

```bash
# インストール
whalebrew install sacloud/terraform
# 実行(-e SAKURACLOUD_ACCESS_TOKEN -e SAKURACLOUD_ACCESS_TOKEN_SECRET -v $PWD:/workdir が指定されている状態となる)
terraform plan
```


## 使い方(docker-composeを使う場合)

#### 1) 以下コマンドで`docker-compose.yml`と環境変数設定ファイルのひな形をダウンロードします。

```bash
curl -L https://github.com/sacloud/terraform-for-sakuracloud-docker/raw/master/docker-compose.yml > docker-compose.yml
curl -L https://github.com/sacloud/terraform-for-sakuracloud-docker/raw/master/env-sample > .env
```

#### 2) (**オプション**)環境変数設定ファイルを編集します。

このファイルで環境変数を設定しておくとterraformコマンド実行時に
必要なオプションを省略できます。

アクセストークン`SAKURACLOUD_ACCESS_TOKEN`とシークレット`SAKURACLOUD_ACCESS_TOKEN_SECRET`の
設定をしておくと便利です。

```bash
vi .env
```

#### 3) docker-composeコマンドの実行

以下コマンドでterraformを起動します。
*.tfファイルはカレントディレクトリに配置してください。

#### `terraform plan`実行例
```bash
docker-compose run --rm terraform plan
```


