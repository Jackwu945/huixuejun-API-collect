# 引言  
## 慧学君的观察日记
****
### 普遍规律
大部分情况下,该网站的api接口是https://hs.huixuejun.com/hs98/public/?service= 后接不同services的名称(如App.Live.Stulives)  
****
### 1. Token(通讯适配符)
+ 大部分情况下post中需要传入一个token(推测是csrf),该token需要带cookie在网页源代码中获取.  

以python为例,代码如下:  
  `token=requests.get('https://s.huixuejun.com/Lessons/Index?task=1&sub=401',cookies=eval(savecookies)).text  
  token=re.findall(r'token = "(.*)";', str(token))[0]`    
其中token变量放在字典中就可以post了.  

+ 需要注意该token每次登陆都会发生变化,传入无效的或者过时的token后api会提示  
`{"ret":411,"msg":"本账号已在其他设备登陆！"}`  
****
