**** 
#show流程
```flow
st=>start: Device页面显现
ed=>end: 结束
upgradeBase=>operation: 升级基站

formatSD=>operation: 格式化sd卡


checkNeedForceUpgrade=>condition: 检查是否需要
                                    强制升级
checkSDCard=>condition: 检查是否SD
                        卡需要格式化


st->checkSDCard(no)->checkNeedForceUpgrade(no)->ed
checkSDCard(yes)->formatSD->checkNeedForceUpgrade(yes)->upgradeBase->ed
```
****

****

