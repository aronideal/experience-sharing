
```javascript
$("#inputEmail3333").change(function(){
    $("#yulan").attr("src",URL.createObjectURL($(this)[0].files[0]));
});
```


// 下边这个待研究
function getObjectURL(file) {
var url = null ;
if (window.createObjectURL!=undefined) { // basic
url = window.createObjectURL(file) ;
} else if (window.URL!=undefined) { // mozilla(firefox)
url = window.URL.createObjectURL(file) ;
} else if (window.webkitURL!=undefined) { // webkit or chrome
url = window.webkitURL.createObjectURL(file) ;
}
return url ;
}
