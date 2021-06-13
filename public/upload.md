以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 上传图片
>https://hs.huixuejun.com/hs98/public/?service=App.Task.UploadImages

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| file[]    | bin  | 图片二进制格式     | 网友说是base64 |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| ret | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | str  | 图片名 | |  

未上传墙,图片一般会保存在 https://hs.huixuejun.com/hs100/public/tmpsource/文件返回的data值 中,在研讨或随测的最后上传需要它的名字.
 
**Eg:**
要上传一个takagi
```python
print('本人还不会如何上传二进制图片,555')
```
回复:
```json
{ret: 200, data: "60c62cc622dba.jpg", msg: ""}
data: "60c62cc622dba.jpg"
msg: ""
ret: 200
```
