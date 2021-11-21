# 控制台实用技巧

## console.assert

> 常用于：断言，用于判断用于验证代码是否符合预期

![image-20211121174100455](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121174100455.png)

## console.clear()

> 常用于：清空控制台输出
>
> 或者使用command +k清除控制台

## console.count([label])

> 常用于：计算代码函数执行次数
>
> console.countReset([label])用于清除console.count的计数

``` javascript
console.count();
console.count('coffee');
console.count();
console.count();
console.countReset();
console.count();
```

![image-20211121174221918](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121174221918.png)

##  console.error

> 常用于：错误调试，方便在控制台分类、错误收集上报等

##  console.group(label) + console.info()

> 常用于：打印信息分组，方便查看
>
> console.groupEnd([label])用于终止分组

![image-20211121180840118](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121180840118.png)

##  console.table(array)

> 常用于：格式化打印信息成表格，易于查看

![image-20211121181720321](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121181720321.png)

## console.time([label])

> 常用于：查看函数执行耗时

![image-20211121181917463](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121181720321-20211121205520853.png)

## console.trace()

> 常用于：查看函数调用栈

![image-20211121182041996](https://raw.githubusercontent.com/Chanran/share-devtool/images/imgs/image-20211121182041996.png)
