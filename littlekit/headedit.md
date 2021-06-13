以下排版参考了 @SocialSisterYi 的 [api文档](https://github.com/SocialSisterYi/bilibili-API-collect/blob/master/login/login_action/password.md)
# 换头像
>https://s.huixuejun.com//Setting/editHead

使用的请求方法:POST  
认证方式：Cookie  

**要传入的参数:**

| 参数名      | 类型 | 内容             |  备注             |
| ----------- | ---- | ---------------- |  ---------------- |        |
| head    | str  | 头像链接     |  |

**json回复：**  
根对象:  
| 字段        | 类型 | 内容                | 备注 |
| ----------- | ---- | ------------------- | ---- |
| status | str  | 状态 | 0失败,1成功|
| msg | str  | 成功信息 | 无论如何都会成功,就是能不能加载出来的问题 |  
 
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
