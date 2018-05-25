**** 
#云存储订阅流程
```flow
st=>start: 准备订阅
ed=>end: 订阅结束

[//]: <> (操作)
getpacks=>operation: 获取套餐列表
selePack=>operation: 选择套餐
getcurpack=>operation: 获取当前套餐
promptCanSUb=>operation: 提示无法订阅
seleDevice=>operation: 选择未订阅的设备
payOrder=>operation: 支付订阅

[//]: <> (条件)
hassubOrPlus=>condition: 是否有订阅或是否
                    有生效的plus套餐
isplus=>condition: 是否是
                    plus套餐
isplus2=>condition: 是否是
                    plus套餐


st->getpacks->hassubOrPlus(yes)->getcurpack->isplus(yes)->promptCanSUb->ed
isplus(no)->seleDevice->payOrder
hassubOrPlus(no)->selePack->isplus2(no)->seleDevice
isplus2(yes)->payOrder->ed

```

****

****


