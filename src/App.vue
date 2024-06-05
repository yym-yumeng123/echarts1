<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  myEcharts.setOption({
    title: {
      text: "ECharts 入门示例",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
      subtext: "ECharts 官网",
      backgroundColor: "pink",
      borderColor: "red",
      borderWidth: 1,
      itemGap: 10,
      x: "center",
      y: "top",
      // textAlign: 'center',
      textStyle: {
        color: "black", // 主标题文字颜色
        fontStyle: "normal", // 主标题文字风格
        fontWeight: "normal", // 主标题文字粗细
        fontFamily: "sans-serif", // 主标题文字字体
        fontSize: 18, // 主标题文字大小
        lineHeight: 30, // 主标题文字行高
        backgroundColor: "red", // 主标题文字背景色
        borderColor: "blue", // 主标题文字边框颜色
        borderWidth: 1, // 主标题文字边框宽度
        padding: 5, // 主标题文字内边距
        shadowColor: "black", // 主标题文字阴影颜色
        shadowBlur: 10, // 主标题文字阴影模糊大小
        shadowOffsetX: 5, // 主标题文字阴影水平偏移
        shadowOffsetY: 5, // 主标题文字阴影垂直偏移
        textBorderColor: "blue", // 主标题文字描边颜色
        textBorderWidth: 1, // 主标题文字描边宽度
        textShadowColor: "black", // 主标题文字描边阴影颜色
        textShadowBlur: 10, // 主标题文字描边阴影模糊大小
        textShadowOffsetX: 5, // 主标题文字描边阴影水平偏移
        textShadowOffsetY: 5, // 主标题文字描边阴影垂直偏移
        textPadding: 5, // 主标题文字描边内边距
        rich: {
          // 富文本
          a: {
            color: "red",
            lineHeight: 30,
          },
          b: {
            color: "blue",
            lineHeight: 30,
          },
        },
      },
    },
    // 提示框
    tooltip: {
      trigger: 'axis', // 触发类型
      show: true, // 是否显示提示框
      axisPointer: {
        type: 'shadow', // 指示器类型
        label: {
          backgroundColor: '#6a7985', // 文字背景颜色
        },
      },
      textStyle: {
        color: 'red', // 文字颜色
      },  
      showContent: true, // 是否显示提示框浮层
      formatter (params) {
        console.log(params)
        return `${params[0].name}: ${params[0].value}`;
      }, // 提示框浮层内容格式器
    },
    // x轴
    xAxis: {
      data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
    },
    // y轴
    yAxis: {},
    // 系列
    series: [
      {
        name: "销量",
        type: "bar",
        data: [5, 20, 36, 10, 10, 20],
      },
    ],
  });
  console.log("Component mounted");
});
</script>

<template>
  <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
  <div ref="myChart" id="main" style="width: 600px; height: 400px"></div>
</template>

<style scoped>
</style>
