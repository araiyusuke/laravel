# laravel

## コンテナを作成する。

docker-compose.ymlがあるディレクトリに移動

```
docker-compose up --build
```

## Laravelをインストール

```

docker-compose exec php bash

composer create-project laravel/laravel [プロジェクト名] --prefer-dist "6.*"

```

_プロジェクト名が、developの場合

_composer create-project laravel/laravel develop --prefer-dist "6.*"

## nginxの設定

docker/nginx/default.confを開く

root /var/www/[プロジェクト名]/public;に修正


```

docker restart laravel_nginx

```

http://localhost:8081にアクセスするとLaravelのホーム画面が表示されたらLaravelのインストールが成功

## LaravelからMYSQLに接続できるようにする

### .env

```
DB_CONNECTION=mysql
DB_HOST=laravel_mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=kjfdslkjfdsfds
```


```
docker-compose exec php bash

cd /var/www/develop

php artisan migrate
```
