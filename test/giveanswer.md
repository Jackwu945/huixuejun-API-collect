以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 获取答题记录
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
