# Vue 3 + Vite

使用 vue3 + echarts 来实现一个简单的数据可视化项目

### title 属性解析

```js
// 标题
title: {
  text: '', // 主标题
  link: '', // 主标题链接
  target: 'self', // 主标题链接打开方式
  subtext: '', // 副标题
  backgroundColor: 'red', // 标题背景色
  borderColor: 'blue', // 标题边框颜色
  borderWidth: 1, // 标题边框宽度
  padding: 5, // 标题内边距
  itemGap: 10, // 主副标题之间的间距
  textStyle: {
    color: 'black', // 主标题文字颜色
    fontStyle: 'normal', // 主标题文字风格
    fontWeight: 'normal', // 主标题文字粗细
    fontFamily: 'sans-serif', // 主标题文字字体
    fontSize: 18, // 主标题文字大小
    lineHeight: 30, // 主标题文字行高
    backgroundColor: 'red', // 主标题文字背景色
    borderColor: 'blue', // 主标题文字边框颜色
    borderWidth: 1, // 主标题文字边框宽度
    padding: 5, // 主标题文字内边距
    shadowColor: 'black', // 主标题文字阴影颜色
    shadowBlur: 10, // 主标题文字阴影模糊大小
    shadowOffsetX: 5, // 主标题文字阴影水平偏移
    shadowOffsetY: 5, // 主标题文字阴影垂直偏移
    textBorderColor: 'blue', // 主标题文字描边颜色
    textBorderWidth: 1, // 主标题文字描边宽度
    textShadowColor: 'black', // 主标题文字描边阴影颜色
    textShadowBlur: 10, // 主标题文字描边阴影模糊大小
    textShadowOffsetX: 5, // 主标题文字描边阴影水平偏移
    textShadowOffsetY: 5, // 主标题文字描边阴影垂直偏移
    textPadding: 5, // 主标题文字描边内边距
    rich: { // 富文本
      a: {
        color: 'red',
        lineHeight: 30
      },
      b: {
        color: 'blue',
        lineHeight: 30
      }
    }
  },
  x: 'center', // 主标题水平对齐方式
  y: 'top', // 主标题垂直对齐方式
  textAlign: 'center', // 主标题文本对齐方式
  textVerticalAlign: 'top', // 主标题文本垂直对齐方式
  triggerEvent: true // 是否触发事件
  left: 10, // 主标题左边距
  right: 10, // 主标题右边距
  top: 10, // 主标题上边距
  bottom: 10, // 主标题下边距
}
```

### tootip 属性解析

```js
tootip: {
  show: true, // 是否显示
  trigger: 'item', // 触发类型
  triggerOn: 'mousemove', // 触发条件
  showContent: true, // 是否显示内容
  backgroundColor: 'red', // 提示框背景色
  borderColor: 'blue', // 提示框边框颜色
  borderWidth: 1, // 提示框边框宽度
  textStyle: { // 提示框文本样式
    color: 'black', // 文字颜色
  },
  formatter: '{a} <br/>{b} : {c}', // 自定义提示框内容
  axisPointer: {
    type: 'line', // 指示器类型 line shadow cross
    axis: 'auto', // 指示器坐标轴
    snap: false, // 是否吸附
    z: 10, // 层级
    label: {
      show: true, // 是否显示
      precision: 0, // 小数精度
      margin: 8, // 间距
      color: 'red', // 文字颜色
      fontStyle: 'normal', // 文字风格
      fontWeight: 'normal', // 文字粗细
      fontFamily: 'sans-serif', // 文字字体
      fontSize: 12, // 文字大小
      lineHeight: 30, // 文字行高
      backgroundColor: 'red', // 文字背景色
      borderColor: 'blue', // 文字边框颜色
      borderWidth: 1, // 文字边框宽度
      padding: 5, // 文字内边距
      shadowColor: 'black', // 文字阴影颜色
      shadowBlur: 10, // 文字阴影模糊大小
      shadowOffsetX: 5, // 文字阴影水平偏移
      shadowOffsetY: 5, // 文字阴影垂直偏移
      textBorderColor: 'blue', // 文字描边颜色
      textBorderWidth: 1, // 文字描边宽度
      textShadowColor: 'black', // 文字描边阴影颜色
      textShadowBlur: 10, // 文字描边阴影模糊大小
      textShadowOffsetX: 5, // 文字描边阴影水平偏移
      textShadowOffsetY: 5, // 文字描边阴影垂直偏移
      textPadding: 5, // 文字描边内边距
      rich: { // 富文本
        a: {
          color: 'red',
          lineHeight: 30
        },
        b: {
          color: 'blue',
          lineHeight: 30
        }
      }
    }
  },
}
```

### legend 图例 属性解析

```js
legend: {
  show: true, // 是否显示
  icon: 'circle', // 图例图标类型 circle rect roundRect triangle diamond pin arrow none
  type: 'plain', // 图例类型 plain scroll
  left: 10, // 图例左边距
  right: 10, // 图例右边距
  top: 10, // 图例上边距
  bottom: 10, // 图例下边距
  width: 'auto', // 图例宽度
  height: 'auto', // 图例高度
  orient: 'horizontal', // 图例布局方式 horizontal vertical
  align: 'auto', // 图例水平对齐方式 auto left center right
  padding: 5, // 图例内边距
  itemGap: 10, // 图例项之间的间距
  itemWidth: 25, // 图例项宽度
  itemHeight: 14, // 图例项高度
  formatter: '{name}', // 格式化图例文本
  selectedMode: true, // 是否可选中
  inactiveColor: '#ccc', // 未选中图例颜色
  selected: { // 默认选中
    '系列1': true,
    '系列2': false
  },
  textStyle: {
    color: 'black', // 文字颜色
    fontStyle: 'normal', // 文字风格
    fontWeight: 'normal', // 文字粗细
    fontFamily: 'sans-serif', // 文字字体
    fontSize: 12, // 文字大小
    lineHeight: 30, // 文字行高
    backgroundColor: 'red', // 文字背景色
    borderColor: 'blue', // 文字边框颜色
    borderWidth: 1, // 文字边框宽度
    padding: 5, // 文字内边距
    shadowColor: 'black', // 文字阴影颜色
    shadowBlur: 10, // 文字阴影模糊大小
    shadowOffsetX: 5, // 文字阴影水平偏移
    shadowOffsetY: 5, // 文字阴影垂直偏移
    textBorderColor: 'blue', // 文字描边颜色
    textBorderWidth: 1, // 文字描边宽度
  }
}
```