# laravel 5.5


## 微信扩展包

> [EasyWeChat](https://github.com/overtrue/laravel-wechat)

    composer require overtrue/laravel-wechat:~4.0

## HTTP扩展包

> [Guzzlehttp](https://github.com/guzzle/guzzle)

    composer require guzzlehttp/guzzle

## 后台扩展包

> [Laravel-admin](http://laravel-admin.org/docs/#/zh/installation)

    composer require encore/laravel-admin 1.5.*

## 部署

1. 时区设置 本地化设置

    > 文件 `wx.hzyuewan.com\config\app.php`

    > `'timezone' => 'UTC'` => `'timezone' => 'PRC'`

    > `'locale' => 'en'` => `'locale' => 'zh-CN'`

1. 索引长度 & MySQL / MariaDB

    > 文件 `wx.hzyuewan.com\app\Providers\AppServiceProvider.php`

    > boot方法 加入 `Schema::defaultStringLength(191)`;

1. 数据库配置 .env文件

    > 修改

        `DB_HOST=127.0.0.1`

        `DB_PORT=3306`

        `DB_DATABASE=wechat`

        `DB_USERNAME=root`

        `DB_PASSWORD=root`

    > 新增

        `APP_LOG=daily`

1. laravel-admin 安装

    > `php artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"`

    > `php artisan admin:install`

    > 默认账号密码 `admin` `admin`

1. laravel-admin-extensions/log-viewer

    > composer require laravel-admin-ext/log-viewer -vvv

    > php artisan admin:import log-viewer

    Open `http://localhost/admin/logs`.
