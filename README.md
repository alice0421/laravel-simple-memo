# **【勉強用】 【作って学ぶ】laravel8とMySQLで作るシンプルメモアプリ（Udemy講座）**

# 概要
Udemy講座の1つである「[【作って学ぶ】laravel8とMySQLで作るシンプルメモアプリ](https://www.udemy.com/course/laravel8mysql/)」の履修用レポジトリ。

[MacOSで作るDockerを用いたLaravel9+Nginx+MySQL環境構築](https://github.com/alice0421/docker-laravel/tree/develop)からCloneした環境を元に作成。

# メモ
## セクション2: 環境構築
### gitの初期化
- `rm -rf .git`でgitから切り離す。
- `git init`でgitと再接続。
- `git remote add origin [追加レポジトリ]`で新たなリモートレポジトリに繋ぐ。

### Dockerでの環境構築（講座とは異なる）
- `docker-compose.yml`のコンテナ名を書き換える（ディレクトリが異なると別のDocker環境が作られる）。
- ルートディレクトリにDocker用の`.env`ファイルを作成する（Clone前のDocker環境のコピペでOK）。
- srcディレクトリにLaravelプロジェクト用の`.env`ファイルを作成する。
  - `.env.example`の中身をコピーして、`php artisan key:generate`する。
- `composer install`を実行する（忘れると`php artisan --version`ができない）。

以上を行うと、Laravel9のWelcomeページが表示される。

## セクション3: メモ機能以外を実装
### マイグレーション
- マイグレーションはファイル作成順に実行される。そのため、外部キーが存在する際にはファイル作成の順番に注意。
  - 今回はusers->memos->tags->memo_tagsの順番。

### ログイン機能
- Laravel9においてLaravel UIは非推奨なため、代わりにLaravel Breezeをインストール。
  - `php artisan breeze:install blade`にすると、bladeを用いたBreezeがインストールされる。
  - 今回はdarkモードを適用させた（`php artisan breeze:install blade --dark`）。後からこのコマンドを打ってもdarkモードにできる。