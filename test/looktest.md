以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 获取所有题目信息
>https://hs.huixuejun.com/hs98/public/?service=App.Task.GetTaskQuestion

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)            | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)    |
| task_id    | str  | 任务id     | 任务id |
| errbj    | str  | 未知     | 好像必为1 |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| ret | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| 一串数字 | num  | 大题 | 使用request处理可能会报错?|

嵌套的字典内的对象由于内容过多,只展示主要内容  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| name | str  | 大题名称 |  |
| pc_end_time/pc_start_time | str  | 用户结束/开始时间 | |
| pc_taskname | str  | 标题 |  |
| set | list  | 题目集 |  |

set列表内元素是字典,字典内容:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| 'task_id' | str  | 任务id |  |
| 'id' | str  | 题目id | |
| 'basetype' | str  | 题型 | 1:单选题,2:多选题 |
| auto | str  | 自动批改 | 1:自动 |
| 'question_no' | str  | 题号 |  |
|'score'|str|分数||
|'titlename'|str|题目说明||  

# 获取试卷图片
>https://hs.huixuejun.com/hs98/public/?service=App.Task.GetTestResource

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)            | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)    |
| task_id    | str  | 任务id     | 任务id |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| ret | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| 一串数字 | num  | 图片地址 | |
| list | list  | 图片地址列表 | |

嵌套的字典内的一串数字对象  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| filename | str  | 文件名 |  |
| is_pic | str  | 是不是图片 | |
| prev_url | str  | 完整地址 |  |
| save_url | str  | 主机内地址 | 砍掉了前面的一二三级域名 |  

list内容:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| 'task_id' | str  | 任务id |  |
| 'title' | str  | 随测名 | |
| 'type' | str  | 图片类型 ||
| uri | str  | 图片地址 | |  

**Eg:**
工事中
```shell

```
回复:
```json

```

