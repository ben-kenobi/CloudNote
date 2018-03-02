**** 
#show流程
```flow
st=>start: 准备显示
ed=>end: dismiss流程
create=>operation: 创建Banner并初始化
invokeShow=>operation: 调用show
removeBlock=>operation: 移除倒数的dismiss Block
addToSuper=>operation: 添加到父View并初始化状态
addToDict=>operation: key为iden添加到Dict
addShowAni=>operation: 添加显示动画
addBlock=>operation: 添加倒数的dismiss Block
show=>operation: 显示

findFromDict=>condition: 使用iden从Dict中查找，是否存在
hasSuper=>condition: 是否已经添加到View

st->findFromDict
findFromDict(yes)->invokeShow->removeBlock->hasSuper
findFromDict(no)->create->invokeShow
hasSuper(yes)->addToDict->addShowAni->addBlock->show->ed
hasSuper(no)->addToSuper->addToDict
```
****

****
#dismiss流程
```flow
st=>start: 准备取消显示
ed=>end: 结束
removeBlock=>operation: 移除倒数的dismiss Block
addDismissAni=>operation: 添加取消动画
removeFromSuper=>operation: 从父View移除
removeFromDict=>operation: 从dict中移除


findFromDict=>condition: 使用iden从Dict中查找，是否存在
hasSuper=>condition: 是否已经添加到View



st->findFromDict
findFromDict(yes)->removeBlock->hasSuper
findFromDict(no)->ed
hasSuper(yes)->addDismissAni->removeFromSuper->removeFromDict->ed
hasSuper(no)->ed
```
****

