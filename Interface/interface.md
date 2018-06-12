## 面向接口编程Demo

```php

<?php

interface js
{
    function ys($a, $b);
}

class Jf implements js
{
    function ys($a, $b)
    {
        return "减法运算......结果为:" . ($a - $b);
    }
}

class China implements js
{
    public $varl = null;//这里直接：public $varl = new nothingx(); 会出错。

    function __construct()
    {
        $this->varl = new nothingx();
    }

    function ys($a, $b)
    {
        return $this->varl->say();
    }
}

class nothingx
{
    function say()
    {
        return "我什么运算都不做...只是为了实现<font color=#990000>
        <b>‘耦合设计模式'</b></font>...我是出来打酱油的......";
    }
}

class test
{
    private $one;
    private $two;

    public function __construct($x, $y)
    {
        $this->one = $x;
        $this->two = $y;
        echo "<font size=20px><strong>面向对象程序设计——接口</font>
        </strong><hr>Class test初始化：<br>
        属性\$one=" . $this->one . "　　属性\$two=" . $this->two . "<hr>";
    }

    function display(js $a)
    {
        return "<font color=#990000><b>用PHP接口技术实现的运算——开始运算啦:
        </b></font><hr>" . $a->ys($this->one, $this->two) . "<hr>";
    }
}

$t = new test(103, 2);
$t1 = new jf;
$t2 = new China;
echo $t->display($t1);
echo $t->display($t2);

```
