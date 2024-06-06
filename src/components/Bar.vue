<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "ECharts 入门示例",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
      subtext: "ECharts 官网",
    },
    // x 轴 參數
    xAxis: {
      // 坐标轴类型: 类目轴
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      // type: "value",
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: '日期',
        type: "bar", // 系列类别
        data: [150, 230, 224, 218, 135, 147, 260], // 对应 y 轴的数据
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="bar1" style="width: 600px; height: 400px"></div>
</template>
