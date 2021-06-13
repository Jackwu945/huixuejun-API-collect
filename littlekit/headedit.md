以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 换头像
>https://s.huixuejun.com//Setting/editHead

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |        |
| head    | str  | 头像链接     | 真的可以上传"外链" |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| status | str  | 状态 | 0失败,1成功|
| msg | str  | 成功信息 | 无论如何都会成功,就是能不能加载出来的问题 |  
 **注意!由于该接口是开发人员的一个思维错误,但指定的外链要是https://hs.huixuejun.com/hs98/public往后的链接.但这足够了,因为研讨和随测的图片都在这级目录之后!**
**Eg:**
更换个研讨里的图片  
```shell
curl 'https://s.huixuejun.com//Setting/editHead' \
--data-urlencode 'head=source/discuss/20210528/60b0667a685bc.jpg' \
```
回复(经过删减):
```json
{'status': 1, 'msg': '头像更换成功'}
```
