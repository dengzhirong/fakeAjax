# JS库：使用隐藏的iframe发送表单提交

>- Author: 邓智容
>- Created: 2017-06-19,  Last-Modified: 2017-06-19
>- 依赖 jQuery或者 Zepto

## 原理：

使用隐藏的iframe提交表单数据，实现无刷新提交和同父域名下的跨域接口访问。

## options参数说明：

参数 | 说 明
-----|-----------
url     | api接口地址 （必填）
type    | 请求method（选填。默认值为get）
data    | 发送的data对象。（选填。默认为空）
blank   | 当前域下blank.html页面的url地址 （选填。默认值为当前页面路径下的blank.html。填写的是绝对路径）
form    | form表单DOM （选填。需要提交的form表单DOM）
success | 表单提交成功后的回调函数，参数为返回的data数据
error   | 表单提交失败后的回调函数

## 使用示例：

```
var submitByIframe = PostByIframe.create({
    url: 'http://example.com/api',
    type: 'post',
    data: {
            a: 12,
            b: 32
        },
    blank: 'http://example.com/blamk.html',
    success: function(res) {
        console.log(res);
    },
    error: function() {
        alert('服务器错误！');
    }
});

// 发送请求
submitByIframe.submit();
```

## 注意事项：

>- 1. 一定要有blank.html，且空白页内设置的document.domain 与 当前页的document.domain 一致；
>- 2. 当前页一定要设置 document.domain；
>- 3. 当前组件跨域只适合父域名相同的跨域接口间的访问；
>- 4. 依赖jQuery或者Zepto，可兼容到IE7；