# 微信开发

## 第二步：验证消息的确来自微信服务器

```

<?php

function checkSignature($token) {
    $signature = $_GET["signature"];
    $timestamp = $_GET["timestamp"];
    $nonce = $_GET["nonce"];
    $tmpArr = array($token, $timestamp, $nonce);
    sort($tmpArr, SORT_STRING);
    $tmpStr = implode($tmpArr);
    return sha1($tmpStr) == $signature;
}

// 微信公众后台填写的Token
$token = 'hello';
// 如果验证正确，则返回参数echostr的内容，否则终止执行
if(checkSignature($token)) {
    echo $_GET['echostr'];
}
exit();

```
