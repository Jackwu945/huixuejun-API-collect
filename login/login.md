# 关于登录  
+ 用代码模拟登录的目标是获取一个cookie,具体作用敬请百度.  
+ 一般情况下,cookie中的值会在完成登录后通过http头中`set-cookie`写入.  
+ 在python的requests库中,完成登录会在 `请求变量.cookie`中  
***
以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 使用账号密码登录
>https://s.huixuejun.com/Home/AjaxLogin  

使用的请求方法:POST  
验证成功后会设置一个`CAKEPHP`的cookie项  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| usernm | num  | 用户登录账号                | 你慧学君的账号        |
| passwd    | str  | 密码     | 你慧学君账号的密码 |

**json回复：**

| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| code | num  | 返回值 | 200:成功<br />500:账号不存在或账号密码错误<br />400:请求错误(推测)  |
| msg | str  | 错误信息 | 没有即成功 |
| tourl | str  | 跳转链接 | 登陆后的主页 |

**Eg:**
用户名为114514 密码为mingh  
```shell
curl 'https://s.huixuejun.com/Home/AjaxLogin  ' \
--data-urlencode 'usernm=114514' \
--data-urlencode 'passwd=mingh' \
```
回复:
```json
{"code":200,"msg":"","toUrl":"..\/Lessons\/Index?task=1&sub=401"}
```
