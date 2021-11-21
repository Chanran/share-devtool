# 断点调试实用技巧

相信大家平常都有用过断点调试，了解以下更多的调试方式可以提高调试效率

## 代码行断点

在"sources"（中文"来源"）的tab找到想要调试的文件和代码

- 点击左侧代码行对应的行号，行号会被高亮

> 最简单的调试方式

<img src="https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211120223139404.png" alt="image-20211120223139404" style="zoom:75%;" />

- 或者在源代码加上"debugger"的方法，再触发函数执行到"debugger"的执行

> 常用于
>
> 1. 移动端Remote调试
> 2. 动态加载的代码调试

```js
console.log('a');
console.log('b');
debugger;
console.log('c');
```

![image-20211120223504193](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211120223441502.png)

## 条件断点调试

给代码某一行右键点击"添加条件断点"，当函数传入的value是2的时候触发断点

> 常用于：
>
> 1. 列表数据调试：比如列表会渲染几百条数据，当只需要取一条数据的值进行调试时
> 2. 多变数据调试：线上、test环境数据多变，很容易被多变的数据干扰调试

![image-20211120223858659](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211120223858659.png)

![image-20211120224053346](/Users/canronglan/Library/Application Support/typora-user-images/image-20211120224053346.png)

## JS DOM节点变更断点调试

给指定的DOM增加断点，可以劫持JS代码的DOM操作，查看当时的调用栈

> 常用于：
>
> 1. 不知道节点被什么地方JS代码修改，用于追踪，断点之后可查看调用栈

- 当前DOM的子树节点的增加、删除

![image-20211121003506256](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121003506256.png)

- 当前DOM的属性的改变

![image-20211121003544047](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121003544047.png)

- 当前DOM被移除

![image-20211121003610130](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121003610130.png)

## XHR断点调试

> 常用于：
>
> 1. 需要调试当时请求特定的资源的调用上下文

![image-20211121004635066](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121004635066.png)

![image-20211121004724371](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121004724371.png)

## 事件触发断点

> 常用于：
>
> 1. 不知道事件在代码什么地方触发
> 2. 想要调试打开页面或者退出页面的事件，比如onload和unload

![image-20211121010609555](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121010609555.png)

![image-20211121010749355](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121010749355.png)

## 异常断点调试

> 常用于：错误断点排查

![image-20211121011723591](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121011723591.png)

![image-20211121011805723](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121011805723.png)

## debug函数断点调试

> 比较小众，功能与代码行断点有些重合

![image-20211121013433412](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121013508584-20211121205316079.png)

![image-20211121013508584](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121013508584.png)

# 参考

https://developer.chrome.com/docs/devtools/javascript/breakpoints