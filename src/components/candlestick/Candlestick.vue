<!-- k 线图 -->
<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "K 线图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    xAxis: {
      // type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      type: "value",
    },
    series: [
      {
        type: "candlestick", // K 线图
        data: [
          [100, 200, 80, 150], // 开盘, 收盘, 最低, 最高
          [150, 220, 70, 200],
          [200, 250, 150, 220],
          [180, 220, 150, 200],
          [200, 300, 180, 250],
          [250, 280, 200, 250],
          [300, 320, 250, 300],
        ],
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="candlestick" style="width: 600px; height: 400px"></div>
</template>