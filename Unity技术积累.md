**修改 tile 图片大小**

https://blog.csdn.net/l1179237106/article/details/117252744



**平台跳跃代码**

https://zhuanlan.zhihu.com/p/466355010

https://doc.weixin.qq.com/doc/w3_AfIA3AaxAGohkK5sIhgQDWUUw0Bfz?scode=AMQAsAcJAAsm14wL1mAfIA3AaxAGo&sid=z9dILYw5WmYuLTNrAKNuWAAA&force_open_in_wx=1





1.Awake不管物体是否被激活都会执行。变量赋值顺序：公共变量 unity 面板 → awake → start

2.start里面的语句执行前提是物体被激活setactive（true）。

3.如果a物体中的awake把b物体关闭setactive（false），那么b中的start语句是不会执行的，没执行到就关掉物体了。


awake不管物体打不打开，全局一次，都会运行。

start要求物体必须打开才能执行，全局一次，之后再打开也不会执行，过了那个全局start时间。

OnEnable是物体（或者说脚本）每一次打开都会执行一次。