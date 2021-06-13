以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 单房间回放信息
>https://hs.huixuejun.com/hs98/public/?service=App.Live.getRoomLive

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |
| token | str  | 当前登录的token(通讯适配符)                | [token获取方式详见引言部分](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/intro/introduction.md)        |
| roomid    | str  | 房间id     | 请参考同级目录的另一篇文章 [戳我](https://github.com/Jackwu945/huixuejun-API-collect/blob/main/live/livesubject.md) |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| ret | num  | 返回值 | 200:成功|
| msg | str  | 错误信息 | 没有这项即成功,有msg则失败 |
| data | list  | 正文 | |  

data对象为一个字典嵌套,第一层索引值为列表科目的索引(从0开始)  
+ 回放一般是分段的,分段多少体现在data长度上

列表里的字典内容如下,鉴于元素内容过多,只展示关键内容.
| 字段         | 内容                | 备注 |
| ----------- | ------------------- | ---- |
| id   | 回放id | |
| url   | 回放地址 | 其格式可能要在格式工厂加工一下 |
| duration | 持续时间 | 单位:秒 |
| title   | 直播间名 |  |
| live_start_time/live_end_time   | 分段开始/结束时间 |  |
|  ...  | 其余内容大部分和历史列表相同 |  |


 
**Eg:**
要查看语文的直播历史记录列表  
```shell
curl 'https://hs.huixuejun.com/hs98/public/?service=App.Live.getRoomLive' \
--data-urlencode 'token=xxx' \
--data-urlencode 'roomid=xxx' \
```
回复(经过删减):
```json
{'ret': 200, 'data': [{'id': '10799', 'domain': 'live13.huixuejun.com', 'app': '21', 'roomid': '60c2a8ddea2b', 'uri': 'http:\\/\\/file.huixuejun.com\\/live\\/m3u8\\/21\\/60c2a8ddea2b\\/2021-06-11-08-53-03_2021-06-11-09-23-03.m3u8', 'duration': '1779.13', 'start_time': '2021-06-11 08:53:02', 'stop_time': '2021-06-11 09:22:42', 'subject_cd': '402', 'subject_name': '高中语文', 'title': '《促织》3', 'status': '2', 'username': '95', 'realname': '马老师', 'class_ids': ',201,202,203,229,', 'class_names': '高一4班,高一5班,高一6班,直播观摩班', 'live_start_time': '2021-05-29 00:00', 'live_end_time': '2023-05-29 00:00:00'}, {'id': '10829', 'domain': 'live13.huixuejun.com', 'app': '21', 'roomid': '60c2a8ddea2b', 'uri': 'http:\\/\\/file.huixuejun.com\\/live\\/m3u8\\/21\\/60c2a8ddea2b\\/2021-06-11-09-23-03_2021-06-11-09-53-03.m3u8', 'duration': '1809.33', 'start_time': '2021-06-11 09:22:42', 'stop_time': '2021-06-11 09:52:52', 'subject_cd': '402', 'subject_name': '高中语文', 'title': '《促织》3', 'status': '2', 'username': '3495', 'realname': '马老师', 'class_ids': ',201,202,203,229,', 'class_names': '高一4班,高一5班,高一6班,直播观摩班', 'live_start_time': '2021-05-29 00:00', 'live_end_time': '2023-05-29 00:00:00'}, {'id': '10835', 'domain': 'live13.huixuejun.com', 'app': '21', 'roomid': '60c2a8ddea2b', 'uri': 'http:\\/\\/file.huixuejun.com\\/live\\/m3u8\\/21\\/60c2a8ddea2b\\/2021-06-11-09-53-03_2021-06-11-09-53-32.m3u8', 'duration': '40.27', 'start_time': '2021-06-11 09:52:51', 'stop_time': '2021-06-11 09:53:32', 'subject_cd': '402', 'subject_name': '高中语文', 'title': '《促织》3', 'status': '2', 'username': '1993495', 'realname': '马老师', 'class_ids': ',201,202,203,229,', 'class_names': '高一4班,高一5班,高一6班,直播观摩班', 'live_start_time': '2021-05-29 00:00', 'live_end_time': '2023-05-29 00:00:00'}], 'msg': ''}
```
