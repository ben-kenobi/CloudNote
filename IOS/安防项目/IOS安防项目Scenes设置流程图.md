**** 
#场景切换流程
```flow
st=>start: 切换场景
ed=>end: 刷新界面展示结果

[//]: <> (操作)
loadingPage=>operation: 更新页面为
                        加载状态
                        
getCam=>operation: 获取当前区域
                    下所有设备

allfaillOp=>operation: 弹出场景切
                        换失败提示
                        
updateToServer=>operation: 更新场景
                            数据到服务器

[//]: <> (手动设置操作)
amnualFlow=>operation: 手动设置流程
                        并等待结果
                        >>在手动流程


[//]: <> (自动设置操作)
scheduleFlow=>operation: Schedule设置
                         流程并等待结果
                >>在schedule流程

[//]: <> (条件)
isAutoMode=>condition: 判断是否是切
                        换为自动状态
hasDevice=>condition: 是否有设备

isAllFail=>condition: 是否全部失败
isScheduleMode=>condition: 是否是Schedule状态


st->getCam->hasDevice(yes)->isAutoMode
hasDevice(no)->updateToServer
isAutoMode(no)->amnualFlow->isAllFail
isAutoMode(yes)->isScheduleMode
isScheduleMode(no)->updateToServer->ed
isScheduleMode(yes)->scheduleFlow->isAllFail
isAllFail(yes)->allfaillOp->ed
isAllFail(no,bottom)->updateToServer->ed
```

****

****


#设置PIRAction流程
```flow
st=>start: 手动设置开始
ed=>end: 手动设置结束


loopCam=>operation: 循环所有设备

getSceneToAction=>operation: 计算当前要设置的场
                                景在每个设备中对
                                应的action配置
                                
SetPirAction=>operation: 对每个设备设置
                        PIRAtion，
                        记录成功失败
                        
piractionRetOp=>operation: 成功的则更
                            新本地数据，
                            失败的记录条数
                            
                            
st->loopCam->getSceneToAction->SetPirAction->piractionRetOp->ed
```
****

****


#设置schedule流程
```flow
st=>start: Schedule设置开始
ed=>end: Schedule设置结束

creaeScheduleID=>operation: 创建ScheduleID

loopCam=>operation: 循环对每个设备
calSchedule=>operation: 将用户设置的shedule数据
                        再根据每个设备配置
                        生成schedule数据
setSchedule=>operation: 设置Schedule和ID
                            并记录结果
scheduleRetOp=>operation: 成功的则更
                            新本地数据，
                            失败的记录条数

hasScheduleID=>condition: 是否有scheduleID


st->hasScheduleID(yes)->loopCam->calSchedule->setSchedule->scheduleRetOp->ed
hasScheduleID(no)->creaeScheduleID->loopCam
```
****

****



#更新sector流程
```flow
st=>start: 更新sector
ed=>end: 更新结束

getFailCam=>operation: 获取当前sector下
                        的设置失败的设备

[//]: <> (手动设置操作)
amnualFlow=>operation: 手动设置流程
                        并等待结果
                        >>在手动流程


[//]: <> (自动设置操作)
scheduleFlow=>operation: Schedule设置
                         流程并等待结果
                >>在schedule流程

[//]: <> (条件)
isAutoMode=>condition: 判断是否是Auto状态
isScheduleMode=>condition: 判断是否是Schedule状态

st->getFailCam->isAutoMode(no)->amnualFlow->ed
isAutoMode(yes)->isScheduleMode(no)->ed
isScheduleMode(yes)->scheduleFlow->ed
```
****


#schedule展示流程
```flow
st=>start: 查看schedule
ed=>end: 更新界面

getScheduleStr=>operation: 根据sector中的schedule
                            数据反向生成schedule数据
filterInvalid=>operation: 循环数据，过滤掉无效数据
st->getScheduleStr->filterInvalid->ed
```
****

#schedule添加流程
```flow
st=>start: 添加或更新schedule
ed=>end: 更新schedule界面


fullGenData=>operation: 根据新设置的数据
                        全量生成Schedule数据
genID=>operation: 生成一个UUID对
                    schedule做标识
updateToserver=>operation: 更新服务器schedule数据
updateScheduleToDevice=>operation: 更新设备shedule流程
                                    >>在schedule流程
isScheduleMode=>condition: 当前区域是否是
                            Schedule模式
serverUpdateRet=>condition: 更新成功


st->fullGenData->genID->updateToserver->serverUpdateRet(no)->ed
serverUpdateRet(yes)->isScheduleMode(no)->ed
isScheduleMode(yes)->updateScheduleToDevice->ed

```
****

#Scenes界面刷新重发失败数据流程
```flow
st=>start: 刷新界面
ed=>end: 展示更新后的界面

reloadData=>operation: 重新加载界面数据
                        并展示成功失败状态
updateSectorFlow=>operation: >>更新sector流程

st->reloadData->updateSectorFlow->ed
```
****






#Scenes添加sector流程
```flow
st=>start: 添加sector
ed=>end: 当前sector切换成
            新增加的sector
            并刷新数据

savetoServer=>operation: 将新sector提交到服务器
failTip=>operation: 失败提示
updateData=>operation: 获取返回数据后
                        更新本地数据
updateSectorFlow=>operation: >>更新sector流程


[//]: <> (条件)
saveResult=>condition: 保存成功



st->savetoServer->saveResult(no)->failTip->ed
saveResult(yes)->updateData->updateSectorFlow->ed
```
****




#Sector修改设备流程
```flow
st=>start: 修改sector下的设备
ed=>end: 刷新界面数据

fullupdateToserver=>operation: 将新数据全量
                                更新到服务器
updateData=>operation: 更新本地数据

updateDefSec=>operation: 更新默认防区
                            >>更新sector流程
updateCurSec=>operation: 更新当前防区
                        >>更新sector流程

[//]: <> (条件)
hasdeduct=>condition: 当前非默认防区且
                    有设备从当前防区移除


st->fullupdateToserver->updateData->hasdeduct(no)->updateDefSec->updateCurSec->ed
hasdeduct(yes)->updateCurSec->ed
```
****

#Sector修改Home Away配置流程
```flow
st=>start: 配置设备场景Action
ed=>end: 刷新界面数据

updateToserver=>operation: 根据当前设置的Scene
                                更新设备配置到服务器
updateData=>operation: 更新本地数据

updateScheduleID=>operation: 生成新的ScheduleID
                                并更新到服务器
updateCurSec=>operation: 更新当前防区
                        >>更新sector流程

[//]: <> (条件)
scheduleEnable=>condition: 是否是schedule模式


st->updateToserver->updateData->scheduleEnable(no)->updateCurSec->ed
scheduleEnable(yes)->updateScheduleID->updateCurSec
```
****


