# shell一些常用技巧

## 字符串处理
1. 字符串截取([参考链接](https://blog.csdn.net/qq_23091073/article/details/83066518))
> 1. 从左向右截取第一个//后的字符串
> >     word=xiaolong//2020-1118//test
> >     echo ${word#*//}
> >     #输出:2020-1118//test
> 2. 从左向右截取最后一个//后的字符串
> >     word=xiaolong//2020-1118//test
> >     echo ${word##*//}
> >     #输出:test  
> 3. 从右向左截取第一个//前的字符串
> >     word=xiaolong//2020-1118//test
> >     echo ${word%//*}
> >     #输出:xiaolong//2020-1118   
> 4. 从右向左截取最后一个//前的字符串  
> >     word=xiaolong//2020-1118//test  
> >     echo ${word%%//*}  
> >     #输出:xiaolong  

   