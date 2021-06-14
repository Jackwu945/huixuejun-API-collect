以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 获取答题记录(缓存)
>https://hs.huixuejun.com/hs98/public/?service=App.Task.CheckAnswersCache

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)      | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
|answrerjson|json|有一定格式的json字典||
| task_id    | str  | 任务id     | 任务id |  

**json字典格式举例**
有多少题该字典长度就多长,每个题格式如下
```{"97692978":{"auto":"1","basetype":"1","answerbody1":"B","pid":"97692978"},.........```

其中字典的key为题目id,[详见获取该信息的接口](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/test/looktest.md),下同
| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| auto | str  |自动改卷||
|basetype|str|题目类型||
| answerbody1    | str  | 回答的字母/文字 | |  
| pid   | str  | 题目id | | 

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
|ret | num  | 返回值 | 200:成功|
| data | str  | 信息 |  |
| msg | str  | 错误信息 | |  

data对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| state | num  | 状态| 推测1即为成功|
 
 # 提交答案
>https://hs.huixuejun.com/hs98/public/?service=App.Task.CheckAnswers

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)      | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
|answrerjson|json|有一定格式的json字典||
| task_id    | str  | 任务id     | 任务id |  
|consumingtime|num|用时|秒|

**json字典格式举例**
同上

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
|ret | num  | 返回值 | 200:成功|
| data | str  | 信息 |  |
| msg | str  | 错误信息 | |  

data对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| state | bool | 状态| true即为成功|
|countscore|num|总分||
|zgscore&checkover|num|主观题得分&总得分||
 
 # 查看你的回答
>https://hs.huixuejun.com/hs99/public/?service=App.Task.GetParseLogInfo

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| task_id    | str  | 任务id     | 任务id |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| code | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| 一串数字 | num  | 题目号 | 使用request处理可能会报错?|
| auto | str  | 是否自动批改(疑) | 1:自动批阅<br />2:手动批阅 |
| basetype | str  | 题目类型(疑) | 1:客观题 (其他研究中) |
| answerbody1 | str  | 客观题选择的答案 | 就是选项的字母<br />主观题则是学生输入的文字 **(推测)** |
| stu_answer_src | str  | 学生的主观题图片回答 | 在服务器中的路径 |
| stu_radio_src/stu_video_src | str  | 学生的录音/录像 | 同样是路径 |
| pid | str  | 进程id | 不知道有啥用(雾) |
 
**Eg:**
工事中
```shell

```
回复:
```json

```
