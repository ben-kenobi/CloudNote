#同步流程

****
```flow
st=>start: 启动应用
ed=>end: 刷新数据

getEufyFromHome=>operation: 通过HM获取所有Eufy设备
setUserIdCharac=>operation: 获取Acc的Userid character并设置
observeRefresh=>operation: 监听服务器数据变化


st->getEufyFromHome->setUserIdCharac->observeRefresh->ed

```
****


