
# Terraform for さくらのクラウド

[Terraform for さくらのクラウド](https://github.com/yamamoto-febc/terraform-provider-sakuracloud)用Dockerイメージ

## `Dockerfile` links

- Terraform 0.7.0系
  - [`0.5.2`(Dockerfile)](https://github.com/yamamoto-febc/terraform-for-sakuracloud-docker/tree/master/0.5.2/)

- Terraform 0.8.0系
  - [`0.6.0`,`latest`(Dockerfile)](https://github.com/yamamoto-febc/terraform-for-sakuracloud-docker/tree/master/0.6.0/)

## 使い方(dockerコマンドを直接使う場合)

### 起動コマンド書式

```bash
docker run -it --rm sacloud/terraform 実行したいコマンド
```

### `terraform plan`実行例
```bash
docker run -it --rm -e SAKURACLOUD_ACCESS_TOKEN -e SAKURACLOUD_ACCESS_TOKEN_SECRET -v $PWD:/work sacloud/terraform plan
```



## 使い方(docker-composeを使う場合)

#### 1) 以下コマンドで`docker-compose.yml`と環境変数設定ファイルのひな形をダウンロードします。

```bash
curl -L https://github.com/yamamoto-febc/terraform-for-sakuracloud-docker/raw/master/docker-compose.yml > docker-compose.yml
curl -L https://github.com/yamamoto-febc/terraform-for-sakuracloud-docker/raw/master/env-sample > .env
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


