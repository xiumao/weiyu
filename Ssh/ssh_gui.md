### SecureCRT

    SecureCRT 超时自动断开连接 很影响工作

    解决办法：

    Options->Session Options->Terminal->Anti-idle->勾选Send protocol NO-OP

    (中文版：选项->会话选项->终端->反空闲->发送协议NO-OP)

    后面的设置时间默认的是60秒，只要小于自动断开连接的时限就可以了。如下图所示：

> [SecureCRT 配置](https://blog.csdn.net/handsomekang/article/details/10037865)
