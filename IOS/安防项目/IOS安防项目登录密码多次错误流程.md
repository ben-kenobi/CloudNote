**** 
#show流程
```flow
st=>start: 登录
ed=>end: 登录结束

tipleftBlockTime=>operation: 提示无法登
                            录剩余时间
deleteThisRecord=>operation: 删除该条记录
addFailCountNTime=>operation: 增加邮箱失败记录，
                            如果是第一次或第5次
                            则记录时间，
                            并根据次数提示用户

checkOver5Times=>condition: 检查邮箱是否
                        失败超过5次
checkOver5Minutes=>condition: 检查邮箱失败
                            是否超5分钟                      
loginToServer=>condition: 登录到服务器
                        并判断是否信息错误




st->checkOver5Minutes(yes)->deleteThisRecord->loginToServer(no)->ed
checkOver5Minutes(no)->checkOver5Times(yes)->tipleftBlockTime->ed
checkOver5Times(no)->loginToServer
loginToServer(yes)->addFailCountNTime

```
****

****

