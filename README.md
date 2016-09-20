### 问题
> 在前后台共同开发项目时, 常常是后台定义好接口,前端按照接口进行开发。经常遇到当前端开发完成而后台接口却未开发完成的情景。此时前端若要进行接口测试, 只能等后台开发完成, 这将浪费大量的时间。前端人员可以使用mockjax和mockJSON，自己mock接口返回数据。

### 简介
> mockjax和mockJSON是两套不同的Javascript Library, 它们都是基于JQuery来开发的,

- mockjax主要是可以针对指定的网址进行mock, 当Ajax呼叫网址时拦截并回传假的数据.
- mockJSON则有点像是Json资料的Data Generater, 根据我们指定的格式随机数生成回传的Json资料.

> mockjax：[Github地址](https://github.com/jakerella/jquery-mockjax)
> mockJSON：[Github地址](https://github.com/mennovanslooten/mockJSON)

### 更多

```
<!DOCTYPE html>
<html>
<head>
  <title>Test</title>
</head>
<body>
  <div id="result"></div>
  <script src="http://code.jquery.com/jquery-1.11.1.min.js"></script>
  <script src="vendor/jquery.mockjax.js"></script>
</body>
</html>
```

> 然后在请求代码之前执行模拟请求的代码，使用该插件提供的 $.mockjax() 方法，暂时先指定2个参数 url 和 responseText：

```
$.mockjax({
  url: '/products/',
  responseText: 'Here you are!'
});
```

> 它会监测具有相同 url 的 Ajax 请求并在请求发出时拦截同时模拟响应，responseText 的值就是模拟的响应内容，这样程序就能继续执行了。

> 当我不再需要模拟请求的时候可以使用 $.mockjax.clear() 方法清除掉：

```
$.mockjax.clear();
```
> 一旦后台服务开发完成，就可以使用该方法清除掉所有模拟请求体验真实的请求效果了。如果不希望一次性清除掉所有的模拟请求，而是针对某个模拟请求，可以传入该模拟请求的 ID，每个模拟请求都会返回一个 ID 值：

```
var idOne = $.mockjax({ }),
    idTwo = $.mockjax({ });

$.mockjax.clear(idTwo);
```
> 这样就把第二个模拟请求清除掉了，保留了第一个。

> 由于 Ajax 请求的 url 地址要和模拟请求的 url 对应，假设页面上有很多请求，每个请求都去模拟的话就会感觉很痛苦，好在，该插件的 url 参数提供了一个通配符 * 方式：

```
$.mockjax({
  url: '/books/*'
});
```

> 这样除了可以匹配 url 地址为 /books/cook 的请求还可以匹配地址为 /books/math 等等更多请求，甚至还可以使用正则表达式进行更复杂的匹配模式：

```
$.mockjax({
  url: /^\/data\/(cook|math)$/i
});
```
> 使用插件的 data 参数可以根据不同的请求数据执行不同的模拟响应：

```
$.mockjax({
  url: '/books/',
  data: {
    type: 'cook'
  },
  responseText: 'You want a cook book!'
});

$.mockjax({
  url: '/books/',
  data: {
    type: 'math'
  },
  responseText: {
    "content": "You want a math book!"
  }
});
```

> 就算是同一个 url 地址当请求的数据不同的时候获得的响应内容也不一样。响应内容除了纯文本字符串，也可以使用 json
格式的字符串。

> 该插件还提供了一个默认参数设置对象 $.mockjaxSettings，没有指定的参数都将使用这些默认值：

```
$.mockjaxSettings = {
  logging:       true,
  status:        200,
  statusText:    "OK",
  responseTime:  500,
  isTimeout:     false,
  throwUnmocked: false,
  contentType:   'text/plain',
  response:      '',
  responseText:  '',
  responseXML:   '',
  proxy:         '',
  proxyType:     'GET',
  lastModified:  null,
  etag:          '',
  headers: {
    etag: 'IJF@H#@923uf8023hFO@I#H#',
    'content-type' : 'text/plain'
  }
};
// 或者
$.mockjaxSettings.contentType = "application/json";
```

> 将默认值修改之后，后面的模拟请求都会使用修改后的值.

### mock.js

```
http://mockjs.com/examples.html
https://github.com/nuysoft/Mock
https://github.com/nuysoft/Mock/wiki
https://segmentfault.com/a/1190000003087224
```
