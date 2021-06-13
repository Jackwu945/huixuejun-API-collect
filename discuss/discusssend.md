以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 上传图片
>https://hs.huixuejun.com/hs98/public/?service=App.Task.UploadTaskDiscuss

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| taskid    | str  | 任务id     |  |
| subid    | str  | 子任务数     | 1开始 |
| pics    | str  | 图片名     | 在上传的[公共接口](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/public/upload.md)里面有数据 |
| resources    | str  | 未知     |  |
| content   | str  | 学生说的话     | 1开始 |

**json回复：**  
根对象:  
sorry,我们的tom没有抓到数据包老鼠~
 
