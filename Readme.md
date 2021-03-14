# docker-terraform

Terraform, aws cliをインストールしたDockerContainerを作成する。

# Features

以下の目的のためdocker-terraformを使用することを想定している。

- Terraformの実行環境をdocker-terraformにすることで
プロジェクトメンバー間での開発環境を統一する。

- 開発環境の構築にかかる時間を短縮する。

# Requirement

* Docker 19.03.12
* docker-compose 1.27.2

# Usage

```bash
git clone https://github.com/hoge/~
cd docker-terraform
export AWS_ACCESS_KEY_ID="xxxxxxxxxxxxx"         
export AWS_SECRET_ACCESS_KEY="xxxxxxxxxxxxxxxxxx"
docker-compose build
docker-compose run --rm terraform bash
```

# Note

### Terraformのバージョンを変更したい場合

デフォルトでインストールするTerraformのバージョンは 0.14.7  
インストールするバージョンを変更したい場合は  
docker-terraform/docker-compose.yamlを編集する。

``` yaml
# docker-compose.yaml

      args: 
        Terraform_version: "インストールしたいTerraformのバージョン"
```

# License

"docker-terraform" is under [MIT license](https://en.wikipedia.org/wiki/MIT_License).

# References

- https://qiita.com/reflet/items/de57ae767c8f368372ba
- https://dev.classmethod.jp/articles/tips-for-aws-cli-v2-on-container/