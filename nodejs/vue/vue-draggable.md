# vue.draggable

源码地址：[github](https://github.com/SortableJS/Vue.Draggable)

## 安装

```
yarn add vuedraggable
npm -i S vuedraggable
```

## 属性

| 属性名           | 说明                                                                       |
| ------------- | ------------------------------------------------------------------------ |
| group         | :group="groupName" 设置为相同组名的组件之间可以相互拖拽                                    |
| sort          | 组内是否可以进行拖拽排序                                                             |
| delay         | 鼠标按下后多久可以进行拖拽                                                            |
| animation     | 过渡动画                                                                     |
| forceFallback | 忽略H5的拖拽行为，若自定义ghostClass chosenClass dragClass样式时，建议forceFallback设置为true |
| ghostClass    | 设置拖动元素的占位符类名,你的自定义样式可能需要加!important才能生效，并把forceFallback属性设置成true         |
| chosenClass   | 被选中目标的样式，你的自定义样式可能需要加!important才能生效，并把forceFallback属性设置成true             |
| dragClass     | 拖动元素的样式，你的自定义样式可能需要加!important才能生效，并把forceFallback属性设置成true              |

## 方法

| 方法名      | 描述                                       |
| -------- | ---------------------------------------- |
| start    | 拖拽开始的回调                                  |
| end      | 拖拽结束的回调                                  |
| remove   | 移除事件                                     |
| update   | 拖拽位置触发的事件                                |
| add      | 从一个组拖拽到另一个组触发的事件                         |
| choose   | 选中元素事件                                   |
| unchoose | 松开鼠标的事件                                  |
| sort     | 位置变化时的事件                                 |
| clone    | 从一个数组拖拽到另外一个数组时触发的事件和add不同，clone是复制了数组元素 |
