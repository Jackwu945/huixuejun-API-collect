以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 获得学习园地→资源
>https://hs.huixuejun.com/hs98/public/?service=App.Task.GetStuDisscuss

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
| list | list  | 资源文件信息 | |
| taskinfo | list  | 任务信息 |  |
| allread | num  | 是否全部完成 | 0:未完成<br />1:已完成 |
| costtime | num  | 用时 | 没有就算null |

  list对象
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| id | num  | 文件id | |
| resource_id | num  | 资源id |  |
| title| str  | 文件名 |  |
| uri | str  | 文件地址 |  |
| type | num  | 文件类型 | 好像都是9 |
| size | num  | 文件大小 | 格式Mb |
| isread | str  | 是否已读 | 0:未完成<br />1:已完成 |

  taskinfo对象
 | 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| web_taskinfo | str  | 大标题 | |
| web_starttime | str  | 开始时间 |  |
| web_endtime| str  | 结束时间 |  |
| web_chaper | str  | 章节 |  |
| web_limited_time | num  | 限时 | 0即无显示 |
 
**Eg:**
要查看id为9366的研讨  
```shell
curl 'https://hs.huixuejun.com/hs98/public/?service=App.Knowledge.GetSourseInfo' \
--data-urlencode 'token=xxx' \
--data-urlencode 'taskid=9366' \
```
回复:
```json
{"ret":200,"data":{"list":[{"id":"11162","resource_id":"3067485","title":"Words and Expressions","uri":"https:\/\/file.huixuejun.com\/hxj_ziyuan\/qita\/yingyu\/5ff821e26016f.mp3","size":"5.61 MB","type":"9","sources":"8","isread":0},{"id":"11163","resource_id":"3067484","title":"Reading and Thinking","uri":"https:\/\/file.huixuejun.com\/hxj_ziyuan\/qita\/yingyu\/5ff821e1a1681.mp3","size":"2.63 MB","type":"9","sources":"8","isread":0},{"id":"11164","resource_id":"3067483","title":"Reading for Writing","uri":"https:\/\/file.huixuejun.com\/hxj_ziyuan\/qita\/yingyu\/5ff821e12e05a.mp3","size":"1.17 MB","type":"9","sources":"8","isread":0}],"taskinfo":{"web_taskinfo":"音频材料：《Unit 2 Wildlife protection》","web_starttime":"2021-01-08 17:10:00","web_endtime":"2021-01-09 17:10:00","web_chaper":"Unit 2 Wildlife protection","web_taskdesc":"","web_limited_time":"0"},"allread":0,"costtime":null},"msg":""}
```
