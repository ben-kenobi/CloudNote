**** 
#登录时确定域名流程
```flow
st=>start: 用户从US登录
ed=>end: 保存用户
            信息在本地
            并登录成功

setDomainByCountryCode=>operation: 根据国家码设置用户域名给服务器(走默认US)
                            

autologin=>operation: 自动登录
                    获取新token

checkLocal=>condition: 检查本地是否
                        有指定域名
checkUserInfoHasDoain=>condition: 检查用户信息
                                    是否有域名

checkIsDefaultDomain=>condition: 检查是否
                    是默认域名

st->checkLocal(yes,right)->ed
checkLocal(no)->checkUserInfoHasDoain(yes)->checkIsDefaultDomain(yes)->ed
checkUserInfoHasDoain(no)->setDomainByCountryCode->checkIsDefaultDomain
checkIsDefaultDomain(no,left)->autologin->ed
```
****

****

