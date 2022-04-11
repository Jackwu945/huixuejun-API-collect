以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 获得研讨任务信息
>https://hs.huixuejun.com/hs105/public/?service=App.Task.GetStuDisscuss

使用的请求方法:POST  
认证方式：Cookie  
无论该任务有无完成都能查看到作答情况,可以干什么不用我多说了吧

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| task_id    | str  | 任务id     | 任务id |
| subid    | str  | 子任务数     | 从1计起|

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| code | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象为所有作品的集合(字典);其中每个字典包含的内容:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| id | num  | 作品id | |
| t_taskmng_id | num  | 不明确,应该也是作品id |  |
| task_id | num  | 任务id |  |
| student_id | num  | 类似于用户uid |  |
| sub_no | num  | 子任务数 |  |
| content | num  | 用户在研讨中的发言 |  |
| content | list  | 用户上传的图片 | list中元素视用户上传图片数为定 |
| resource | str  | 未知 |  |
| creat_time | str  | 上传时间 |  |
| picsrc | str  | 用户头像地址 |  |
| realname | str  | 真名 |  |
| zan | list  | 赞 |  |
| comment | list  | 评论 |  |

**Eg:**
要查看id为13852的研讨  
```shell
curl 'https://hs.huixuejun.com/hs98/public/?service=App.Task.GetStuDisscuss' \
--data-urlencode 'token=xxx' \
--data-urlencode 'taskid=13852' \
--data-urlencode 'subid=1' \
```
回复(鉴于涉及真名,故只显示部分且稍作修改):
```json
 {"ret":200,"data":[{"id":"6710","t_taskmng_id":"1340881","task_id":"13852","student_id":"3001988","sub_no":"1","content":"三分钟写成的屑作","pics":["https:\/\/hs.huixuejun.com\/hs98\/public\/source\/discuss\/20210609\/60c07ea282071.jpeg"],"resource":[],"create_time":"2021-06-09 16:41:36","delete_flag":"1","picsrc":"https:\/\/hs.huixuejun.com\/hs98\/public\/image\/head\/userhead10.png","realname":"jackwu","zan":["0","0","0"],"comment":[],"Spot":0}
```
