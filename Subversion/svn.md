# subversion

## export

> svn  export  [-r 版本号]   (url或目录或文件的全路径)  [本地目录全路径] --username --password --no-auth-cache

## svn help

> svn export --help

## 创建分支或者标签

> svn copy url(trunk) url(branches/tags) -m "add 1.0 released" --username --password --no-auth-cache

## 删除分支或者标签

> svn rm url(branches/tags) -m "rm 1.0 released" --username --password --no-auth-cache

## 获取分支或者标签信息

> svn info url(branches/tags) --username zhangzhenlong --password zhangzhenlong0416 --no-auth-cache



    1. 本地开发完成 提交svn

    2. svn copy 打tags  查看单个tag svn info url(tag) 并获取tag中的Last Changed Rev: 1

    3. 线上发布 svn export -r 1 url(tag)

    4. 第二次发布 svn copy 打tags   查看单个tag svn info url(tag) 并获取tag中的Last Changed Rev: 2

    5. 线上发布 svn export -r 2 url(tag)

    6. 回滚 查看所有tags svn info url(tags) 获取前一个tag的版本号 1  svn export -r 1 url(tags)



    管理员

        用户 CURD

        项目 CURD

    发布记录

        测试按钮 发布代码到测试机器

            自动生成版本号

        上线按钮 发布代码到线上机器（下拉选版本）

        回滚按钮 可以回滚到指定版本（下拉选版本）
