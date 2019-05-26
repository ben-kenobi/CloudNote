**** 
#登录时确定域名流程
```flow
st=>start: 用户登录
ed=>end: 保存用户
            信息
ed2=>end: 登录
        失败
        并
        处理
        错误
        码

setDomainByCountryCode=>condition: <<获取国家码>>设置
                            用户域名给US服务器
                            

autologin=>condition: 从域名登录,
                        是否成功

checkLocal=>condition: 检查本地是否
                        有指定域名
checkUserInfoHasDoain=>condition: 从US登录获取用户信息
                                并检查是否有域名

checkIsDefaultDomain=>condition: 检查用户域名是否是US

st->checkLocal(yes,right)->autologin(no)->ed2
checkLocal(no)->checkUserInfoHasDoain(yes)->checkIsDefaultDomain(yes)->ed
checkUserInfoHasDoain(no)->setDomainByCountryCode(yes)->checkIsDefaultDomain
checkIsDefaultDomain(no,left)->autologin(yes)->ed
setDomainByCountryCode(no)->ed2
```
****



#获取国家码流程
```flow
st=>start: 开始定位
ed=>end: 返回国家码
ed2=>end: 返回失败

startLocating=>operation: 开始定位
reverseLocation=>condition: 获取定位并解析
locationAuth=>condition: 定位权限申请

st->locationAuth(yes)->startLocating->reverseLocation(yes)ed
locationAuth(no)->ed2
reverseLocation(no)->ed2

```
****

****

