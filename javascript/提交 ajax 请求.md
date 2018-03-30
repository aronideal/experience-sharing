
## 基于 jQuery

#### 提交 application/json 请求

服务端

```
请求方法：  POST

接收：      contentType="application/json; charset=UTF-8"
```

客户端

```javascript
$.ajax({
    url: '...',
    type: 'POST',
    data: JSON.stringify({
        param1: 'val-1',
        param2: 'val-2'
    }),
    dataType: 'json',
    contentType: 'application/json; charset=UTF-8',
    success: function(data, textStatus, jqXHR) {
        ...
    }
});
```
