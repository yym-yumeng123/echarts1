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