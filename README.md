# プロジェクトセットアップ手順

この手順に従ってプロジェクトのセットアップを行ってください。

```bash
# プロジェクトのルートディレクトリに移動
cd fmx-supply-mgmt

# Dockerを使用してComposerの依存関係をインストール
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs

# Dockerコンテナをバックグラウンドで起動
./vendor/bin/sail up -d

# .env.exampleをコピーして.envファイルを作成
cp .env.example .env

# Sail環境でシェルにアクセス
./vendor/bin/sail shell

# Sailシェル内でComposer依存関係を再インストール
composer install

# Laravelアプリケーションキーを生成
php artisan key:generate

# データベースマイグレーションを実行
php artisan migrate

# Vue 3をインストール
npm install vue@3

# Viteプラグインをインストール
npm install @vitejs/plugin-vue

# 開発サーバーを起動
npm run dev

# ローカルサーバーにアクセス
http://localhost
