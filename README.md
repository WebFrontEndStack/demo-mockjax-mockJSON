### 问题
> 在前后台共同开发项目时, 常常是后台定义好接口,前端按照接口进行开发。经常遇到当前端开发完成而后台接口却未开发完成的情景。此时前端若要进行接口测试, 只能等后台开发完成, 这将浪费大量的时间。前端人员可以使用mockjax和mockJSON，自己mock接口返回数据。

### 简介
> mockjax和mockJSON是两套不同的Javascript Library, 它们都是基于JQuery来开发的,
- mockjax主要是可以针对指定的网址进行mock, 当Ajax呼叫网址时拦截并回传假的数据,
- mockJSON则有点像是Json资料的Data Generater, 根据我们指定的格式随机数生成回传的Json资料.
mockjax：[Github地址](https://github.com/jakerella/jquery-mockjax)
mockJSON：[Github地址](https://github.com/mennovanslooten/mockJSON)
