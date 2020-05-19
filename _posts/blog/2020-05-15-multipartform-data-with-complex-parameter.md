---
layout: post
title: MultipartForm Data With Complex Parameter
categories: [java]
description: 
keywords: MultipartForm Data, FormData
typora-root-url: ..\..
---
鉴于网上的示例大多是随手复制粘贴转载的代码，故此markdown一下，方便你我他。


# 简述

> @RequestParam 用于处理name-value形式的表单数据
>
> @RequestPart 用于处理更为复杂的内容，如：JSON，XML
>
> 详情见org.springframework.web.bind.annotation.RequestPart注解说明
>
> FormData 对象的使用，[link](https://developer.mozilla.org/zh-CN/docs/Web/API/FormData/Using_FormData_Objects)

# 后端代码（JAVA）

```java
import com.alibaba.fastjson.JSONObject;
import io.choerodon.swagger.annotation.Permission;
import io.swagger.annotations.ApiOperation;
import lombok.Data;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;

import java.util.List;

/**
 * Demo Controller
 *
 * @author Holinc
 */
@RestController("demoController.v1")
@RequestMapping("/api/demo")
public class DemoController {

    /**
     * @param type       URL参数
     * @param q          URL参数
     * @param text       一般文本参数
     * @param jsonString JSON本文参数
     * @param user       对象参数
     * @param blogList   对象参数
     * @param file       文件
     * @see org.springframework.web.bind.annotation.RequestParam
     * @see org.springframework.web.bind.annotation.RequestPart
     */
    @ApiOperation(value = "附件上传")
    @PostMapping(value = "/{type}/upload-attachment")
    public ResponseEntity uploadAttachment(
            @PathVariable(value = "type") String type,
            @RequestParam(value = "q", required = false) String q,
            @RequestPart(value = "text", required = false) String text,
            @RequestPart(value = "jsonString", required = false) String jsonString,
            @RequestPart(value = "user", required = false) User user,
            @RequestPart(value = "blogList", required = false) List<Blog> blogList,
            @RequestPart(value = "file", required = false) MultipartFile file) {

        System.out.println("=================我是附件===============");
        System.err.println(file.getOriginalFilename() + "<>" + file.getSize());

        System.out.println("=================我是URL参数===============");
        System.err.println(type);
        System.err.println(q);

        System.out.println("=================我是文本参数===============");
        System.err.println(text);
        System.err.println(jsonString);

        System.out.println("=================我是对象参数===============");
        System.err.println(JSONObject.toJSONString(user));
        System.err.println(JSONObject.toJSONString(blogList));

        return ResponseEntity.ok("后端已成功接收带参数的附件");
    }

    @Data
    static class User {
        private String username;
        private String password;

    }

    @Data
    static class Blog {
        private String title;
        private String content;
        private User user;
    }
}

```

```shell
###模拟请求参数
POST http://localhost:9120/api/demo/image/upload-attachment?q=QueryStringParameter
Content-Type: multipart/form-data; boundary=WebAppBoundary

--WebAppBoundary
Content-Disposition: form-data; name="text"
Content-Type: text/plain

我是text文本参数啊
--WebAppBoundary
Content-Disposition: form-data; name="jsonString"
Content-Type: text/plain

{"text":"我是文本参数啊"}
--WebAppBoundary
Content-Disposition: form-data; name="user"
Content-Type: application/json

{"username":"Tom","password":"Jerry"}
--WebAppBoundary--
Content-Disposition: form-data; name="blogList"
Content-Type: application/json

[{"title":"section01","content": "content01","user": {"username":"Tom","password":"Jerry"}}]
--WebAppBoundary--
Content-Disposition: form-data; name="file"; filename="http-client.cookies"

< http-client.cookies
--WebAppBoundary--
```

# 预期结果（Console）：

控制台输出：

![image-20200515204751568](/images/posts/java/image-20200515204751568.png)

# 前端代码（JavaScript）

懒得在工程里写示例，直接Chrome Console开撸，效果也差不多，详情见图一、图二、图三。代码片段如下：

```javascript
{

let formData = new FormData();

formData.append("text", '我是文本参数啊');
formData.append("jsonString", '{"text":"我是文本参数啊"}');

let user = {"password":"Jerry","username":"Tom"};
// 复杂对象须指定Content-Type，后台通过JSON解析，所以指定"application/json"。不指定的话，会报错Content type not supported
var blob = new Blob([JSON.stringify(user)], { type: "application/json"});
formData.append("user", blob);

let blogList = [{"content":"content01","title":"section01","user":{"password":"Jerry","username":"Tom"}}]
let blob2 = new Blob([JSON.stringify(blogList)], { type: "application/json"});
formData.append("blogList", blob2);

let myfile = document.getElementById('myfile').files[0];
formData.append("file", myfile);

var oReq = new XMLHttpRequest();

oReq.open("POST", "http://localhost:9120/api/demo/image/upload-attachment?q=QueryStringParameter");
oReq.onload = function () { 
    // 请求结束后,在此处写处理代码
    console.log(oReq.response);
};
oReq.send(formData);

}
```

图一：浏览器模拟带参数附件上传

![image-20200515211343273](/images/posts/java/image-20200515211343273.png)

图二：请求Header示例

![image-20200515211529222](/images/posts/java/image-20200515211529222.png)

图三：请求Header示例，view source看到的信息类似前文提到的后端模拟参数

![image-20200515211749604](/images/posts/java/image-20200515211749604.png)

参考资料：

- <https://developer.mozilla.org/zh-CN/docs/Web/API/FormData/Using_FormData_Objects>