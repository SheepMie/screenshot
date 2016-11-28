# screenshot
screenshot by cropper</br>
First tkanks to the author of cropper.</br>
由于canvas不能使用本地图片最为img.url，这里使用了base64作为url。</br>
cropper内容请移步https://github.com/fengyuanchen/cropper/<br>

/*该方法问题*/
只能改变第一张图，再做改变的时候不能再改变。。。而且用的是base64位，转化数据庞大，不宜作为项目使用。

该版本只做为原理理解，cropper已经对canvas的blob转化做了封装，具体可以使用https://github.com/fengyuanchen/croppe/ 已做了详细介绍，其中main.js可以作为配置文件，按钮工具等按需加载。其中ajax上传的时候可能按版本不同而导致不能上传，提交方法可改成type:"post"。注意的是：手机移动端好像不支持HTMLCanvasElement.toBlob，所以需要手动修改，先把canvas数据转成base64,再通过方法转换成blob形式。

function dataURItoBlob(dataURI) {     //转二进制，便于上传
    var byteString = atob(dataURI.split(',')[1]);
    var mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0];
    var ab = new ArrayBuffer(byteString.length);
    var ia = new Uint8Array(ab);
    for (var i = 0; i < byteString.length; i++) {
        ia[i] = byteString.charCodeAt(i);
    }
    return new Blob([ab], {type: mimeString});
}
