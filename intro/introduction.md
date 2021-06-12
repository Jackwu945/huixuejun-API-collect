# 引言  
### 慧学君的观察日记
****
### 普遍规律与特殊规律
大部分情况下,该网站的api接口是https://hs.huixuejun.com/hs98/public/?service= 后接不同services的名称(如App.Live.Stulives)  
* 登录采用了另外的接口,[详见] (https://github.com/Jackwu945/huixuejun-API-collect/blob/main/login/login.md)
****
# 注意事项
***1.Token(通讯适配符)***
+ 大部分情况下post中需要传入一个token(棺方说法是`通讯适配符`,但我推测其起到`csrf`的作用),该token需要带cookie在网页源代码中获取.  

以python为例,代码如下:  
  `token=requests.get('https://s.huixuejun.com/Lessons/Index?task=1&sub=401',cookies=eval(savecookies)).text  
  token=re.findall(r'token = "(.*)";', str(token))[0]`    
其中token变量放在字典中就可以post了.  

+ 需要注意该token每次登陆都会发生变化,传入无效的或者过时的token后api会提示  
`{"ret":411,"msg":"本账号已在其他设备登陆！"}`  

***2.编码***  
+ 慧学君的json回复中使用了unicode编码,需要将重新编码成`unicode-escape`才能看到正常中文内容.
****
