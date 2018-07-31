### 1. 扫码

初版

```
dd.biz.util.scan({
    type: "qrCode",
    onSuccess: function(data) {
        // data =>{ text: 扫描到的文字} 
    },
   onFail: function(error) {
   }
})
```

改版

```
var scanType = 'qrCode';
YBB.hybrid.util.scan(scanType).then(function(result) {
    // result = {text: 'text text'}
    console.log(result);
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| text | String | 扫描到的内容 |

### 2. 选择图片

初版

```
dd.device.notification.selectImg ({
    cancelButton: “取消”，
    otherButtons: [“拍照”,”相册”]，
    onSuccess: function(data) {
        // data => {"imgPath":path} 
    },
    onFail: function(error) {}
})
```

改版

```
var params = {
    cancelButton: '取消',
    otherButtons: ['拍照', '相册']
};

YBB.hybrid.device.selectImg(params).then(function(info) {
    // info.imgPath 为本地地址
    console.log(info.imgPath);
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| imgPath | String | 图片在手机的绝对路径 |

### 3. 选择图片，回传网络地址

初版

```
dd.device.notification.chooseImage ({
    cancelButton: “取消”，
    otherButtons: [“拍照”,”相册”]，
    onSuccess: function(data) {
        // data => {result:"true", picPath:"http://xxxx"} 
    },
    onFail: function(error) {}
})

```

改版

```
var params = {
    cancelButton: '取消',
    otherButtons: ['拍照', '相册']
};

YBB.hybrid.device.chooseImg(params).then(function(info) {
    // info = {result: boolean, picPath: string}
    // info.picPath 为网络地址
    console.log(info.picPath);
});
```

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| result | String | 字符串‘true’ |
| picPath | String | 图片http地址 |

### 4. 定位

### 5.隐藏导航栏

### 6.显示导航栏

### 7.设置导航栏标题

### 8.关闭当前浏览器页面

### 9. 设置导航栏分段控制器

### 10.打电话

```
dd.biz.telephone.call({
    corpId: '123456',
    onSuccess: function(data) {},
    onFail: function(error) {}
})
```

参数说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| corpId | String | 电话号码 |

返回说明：无返回

### 11. 设置导航栏右按钮

初版

```
dd.biz.navigation.setRightBtn({
    show: false,
    control: true,
    text: "send",
    onSuccess: function(data) {
        //如果control为true，则onSuccess将在发生按钮点击事件被回调 
    },
    onFail: function(error) {}
});
```

改版

```
var isShow = true; // 是否显示
var options = {
    text: 'string', // 按扭文字
    icon: 'string' // 可选的，icon 图片url
};
YBB.hybrid.navigation.setRightBtn(isShow, options).click(function() {
   console.log('按扭被点击了'); 
});
```

参数说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| show | Boolean | 控制按钮显示 |
| control | NSInterger | 是否控制点击事件 |
| text | String | 按钮标题 |
| icon（改版后新增） | String | 按钮图片url |

返回说明：可选返回 currentButtonTitle ， 但必须有 js 的回调

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| currentButtonTitle | String | 按钮标题 |

### 12. 设备唯一标识

初版

```
dd.device.base.getUUID ({
    onSuccess: function(data) {
       // data=> {uuid : 112233...566} 
    },
    onFail: function(error) {}
})
```

改版

```
YBB.hybrid.device.getUUID().then(function(info) {
   console.log(info.uuid); 
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| uuid | String | 设备唯一标识 |

### 13. 授权（初版不存在，改版后新增）

```
var targetUrl = 'http://user.test.com';
YBB.hybrid.user.authorization(targetUrl).then(function(data) {
    /**
    * data = {
    *   state: string;
    *   code: string;
    * }
    */
    console.log(data);
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| code | String | 授权码 |

### 14. 认证（初版不存在，改版后新增）

```
var appId = 'appId';
YBB.hybrid.user.certification(appId).then(function(data) {
    /**
    * data = {
    *   certSuccess: string;  // '0' 失败， '1' 成功，'2'审核中
    *   username: string; // 用户名
    *   idCardNo: string; // 身份证号码
    *   mobile: string; // 手机号码
    * }
    */
    console.log(data); 
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| idCardNo | String | 身份证 |
| username | String | 姓名 |
| mobile | String | 手机号 |
| certSuccess  | String | 认证结果 0 -失败 ， 1- 成功 |

### 15. 登录

```
YBB.hybrid.user.login();
```

返回说明：无返回

### 16.获取IP

```
YBB.hybrid.util.getIP().then(function(response) {
    console.log(response.clientIP);
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| clientIP | String | IP地址 |

### 17. 打开外部应用

### 18. 获取APP当前版本

```
YBB.hybrid.util.getAppVersion().then(function(result) {
    console.log(result.appVersion);
    console.log(result.updateUrl);
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| appVersion | String | 版本号 |
| updateUrl | String | 更新地址 |

### 19. 眼纹识别（二次扫脸）

```
// params 是可选的
var params = {
    certType: '',  // 刷脸方式 取值：字段不传默认为 - 三版, zhima- 芝麻认证, ps - 公安, ss - 社保
    certName: '',   // 刷脸人姓名
    mobile: '',     // 手机号(暂只有公安刷脸需要)
    certNo: ''     // 刷脸人身份证
};
YBB.hybrid.user.eyePatternRecognition(parmas).then(function(result) {
    // result = { code: number, key?: any }
    console.log(result); 
});
```

返回说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| code | Number | 0-成功，1-失败 ，2-审核中 |
| psIguid | String | 公安认证返回的IGUID |

### 20. 分享

初版

```
dd.biz.util.share({
    arg:{
      “titleStr”:”分享标题”,
      “contentStr”:”分享内容”,
      “imageStr”:”分享图片路径”,
      “shareUrlStr”:”分享链接”
     },
    onSuccess : function(data) {},
    onFail : function(error) {}
})
```

改版

```
var args = {
    title: '标题', // 标题
    content: '分享内容', // 分享内容
    imageUrl: 'http://test.user.com/a.jpg', // 分享图片地址
    targetUrl: 'http://test.user.com/target', // 分享跳转的目标地址
    description: '' // 运营文案 
};
YBB.hybrid.util.share(args).then(function() {
    console.log('分享成功！');
}).cache(function(error) {
    console.log(error);
    console.log('分享失败！');
})
```

参数说明

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| titleStr | String | 分享标题 |
| contentStr | String | 分享内容 |
| imageStr | String | 分享图片路径 |
| shareUrlStr | String | 分享链接 |
| description | String | 活动标题 |

返回说明：无返回值

