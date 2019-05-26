#p2p下发指令流程

****
```flow
st=>start: 发送操作指令
ed=>end: 回调操作结果

connect=>operation: <<执行连接>>
exeCmd=>operation: 执行发送操作指令
disconnect=>operation: 断开连接
log=>operation: 记录结果
operRes=>operation: 返回操作结果


isConnect=>condition: 是否连接
connectSuc=>condition: 判断连接结果是否成功
needReconnect=>condition: 是否重连,依据返回值
                            和重连次数判断



st->isConnect
isConnect(yes)->exeCmd->operRes->needReconnect
isConnect(no)->connect->connectSuc(no)->needReconnect(yes,right)->disconnect->isConnect
connectSuc(yes)->exeCmd
needReconnect(no)->log->ed
```
****


#执行连接流程

****
```flow
st=>start: 开始连接
ed=>end: 返回结果

getAppConn=>operation: 获取初始化串

init=>operation: 初始化
connect=>operation: 连接
log=>operation: 记录结果


hasAppConn=>condition: 是否有初始化串
initStrGetSuc=>condition: 是否获取成功
hasInitialized=>condition: 是否初始化
initSucWithinCount=>condition: 三次尝试次数内是否成功
isBaseOnline=>condition: 检查基站是否在线

st->hasAppConn(no)->getAppConn->initStrGetSuc(yes)->hasInitialized
initStrGetSuc(no)->log
hasAppConn(yes)->hasInitialized
hasInitialized(yes)->isBaseOnline
hasInitialized(no)->init->initSucWithinCount(yes)->isBaseOnline
initSucWithinCount(no)->log
isBaseOnline(yes)->connect->log
isBaseOnline(no)->log->ed
```
****




#设置指令
```sequence
App->BS: 建立连接
BS-->App: 返回结果
App->BS: 发送指令
BS->Cam: 设置给Cam
Cam-->BS: 返回结果
BS->Server: 状态同步到后台
Server-->BS: 返回结果
BS-->App: 返回指令结果
Note left of App: 更新本地数据并刷新界面
```


