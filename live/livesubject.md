以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 科目回放列表
>https://hs.huixuejun.com/hs98/public/?service=App.Live.getLiveHistory

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| subject_cd    | str  | 科目代码     | 401:数学<br />402:语文<br />403:英语<br />404:物理<br />405:化学<br />406:生物<br />407:政治<br />408:历史<br />409:地理<br />410:非文<br /> |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| ret | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象为一个字典嵌套,第一层索引值为列表科目的索引(从0开始)  

第二个列表内容如下,鉴于元素内容过多,只展示关键内容.
| 字段         | 内容                | 备注 |
| ----------- | ------------------- | ---- |
| id   | 课程id | |
| subject_cd   | 科目代码 | 同表一 |
| subject_name | 科目名字 |  |
| title   | 直播间名 |  |
| start_time   | 课程开始时间 |  |
| end_time   | 课程结束时间 |  |
| username   | 教师用户名 |  |
| realname   | 教师名 |  |
| class_ids/class_names  | 班级id/班级名 |  |
| created   | 创建时间 |  |
| real_started/real_ended   | 实际的开始/结束时间 |  |
| **roomid**   | 房间号 | **是获取直播信息的关键元素** |

 
**Eg:**
要查看语文的直播历史记录列表  
```shell
curl 'https://hs.huixuejun.com/hs98/public/?service=App.Live.getLiveHistory' \
--data-urlencode 'token=xxx' \
--data-urlencode 'subject_cd=402' \
```
回复(只展示部分,经过删减):
```json
{"ret":200,"data":[{"id":"3087","subject_cd":"402","subject_name":"\u9ad8\u4e2d\u8bed\u6587","title":"\u300a\u4fc3\u7ec7\u300b3","start_time":"09:00","end_time":"09:45","status":"2","username":"1145141919810","realname":"\u8001\u5e08","class_ids":",201,202,203,229,","class_names":"\u9ad8\u4e004\u73ed,\u9ad8\u4e005\u73ed,\u9ad8\u4e006\u73ed,\u76f4\u64ad\u89c2\u6469\u73ed"
```
