# apidoc


## STEP1 git和node安装（node带有npm）

> [git 默认安装](https://git-scm.com/downloads)

> [node 安装教程](http://www.runoob.com/nodejs/nodejs-install-setup.html)


node是否安装成功  cmd命令输入

node --version node是否安装

npm --version npm是否安装

path 查看环境变量 node是否全局可用

## STEP2 安装apidoc

npm install apidoc -g 全局安装

apidoc -h apidoc是否安装

apidoc -i myapp/ -o apidoc/ 把myapp的api文档生成到apidoc目录下

## STEP3 DEMO

新建文件夹example

在example中新建配置文件apidoc.json

apidoc.json写入内容

```json

{
  "name": "DEMO",
  "version": "0.0.1",
  "description": "DEMO_DESCRIPTION",
  "title": "DEMO_TEST",
  "url" : "https://developer.github.com/v3/"
}

```

example新建demo.php写入代码

```

<?php
/**
 * @api {get} /user/:id Request User information
 * @apiName GetUser
 * @apiGroup User
 *
 * @apiParam {Number} id Users unique ID.
 *
 * @apiSuccess {String} firstname Firstname of the User.
 * @apiSuccess {String} lastname  Lastname of the User.
 *
 * @apiSuccessExample Success-Response:
 *     HTTP/1.1 200 OK
 *     {
 *       "firstname": "John",
 *       "lastname": "Doe"
 *     }
 *
 * @apiError UserNotFound The id of the User was not found.
 *
 * @apiErrorExample Error-Response:
 *     HTTP/1.1 404 Not Found
 *     {
 *       "error": "UserNotFound"
 *     }
 */

 ```

 ## cmd命令行运行

 > `apidoc -i example/ -o apidoc/``

 打开apidoc里面的index.html即可看见接口文档
