# laravel

## laravel包 安装

    composer require barryvdh/laravel-debugbar:~2.4

    composer require barryvdh/laravel-ide-helper

    composer require guzzlehttp/guzzle

    composer require arcanedev/log-viewer ^4.4

    composer update


## laravel 配置

    1. sudo chmod -R 777 storage

    2. sudo chmod -R 777 bootstrap/cache

    3. sudo cp .env.example .env

    4. php artisan key:generate

    5. jianshu/config/app.php

        'timezone' => 'PRC',

## 配置迁移命令生成的默认字符串长度

    Schema::defaultStringLength(191);

## laravel 使用

    路由 route

    模板 blade

    控制器 controller

    数据迁移 migration

        php artisan make:migration create_posts_table

        php artisan migrate

    模型 model

        1. 模型创建
            php artisan make:model Post

            Schema::create('posts', function (Blueprint $table) {
                $table->increments('id');
                $table->string('title', 100)->default("");
                $table->text('content');
                $table->integer('user_id')->default(0);

                $table->timestamps();
            });

        2. 模型关联

            一对一 hasOne 用户  手机

            一对多 hasMany 文章 评论

            一对多反向 belongsTo 评论 文章

            多对多 belongsToMany 用户 角色

            远层一对多 hasManyThrough 国家 作者 文章

            多态关联 morphMany 文章/视频 评论

            多态多对多 morphToMany 文章/视频 标签

        3. 模型预加载

            APP\Book::with('author')->get();

            $book->load('author');

            模型关联计数

            App\Post::withCount('comments')->get();

    数据填充 faker seed

        jianshu/database/factories/UserFactory.php

        $factory->define(App\Post::class, function (Faker $faker) {
            return [
                'title' => $faker->sentence(6),
                'content' => $faker->paragraph(10),
            ];
        });
    命令行 tinker            

        php artisan tinker

        factory(App\Post::class,10)->create();

    分页 paging


    开发流程

        列表 index

            分页

            页面显示字符截断 str_limit

        详情 show

        新增 create

            控制器

            csrf

            保存model create

            验证和错误提示

            错误提示本地化

        修改 edit update

            
            `{{ method_field('PUT') }}`

            `{{ csrf_field() }}`

        删除 delete

## 参考资料

> [laravle文档](https://laravel-china.org/docs/laravel/5.4)

> [bootscrap文档](https://v3.bootcss.com/)

> [faker文档](https://github.com/fzaninotto/Faker)

> [carbon文档](http://carbon.nesbot.com/docs/)
