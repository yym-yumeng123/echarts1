<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "散点图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    xAxis: {
      type: "value",
    },
    yAxis: {
      type: "value",
    },
    legend: {
      data: ["散点"],
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "散点",
        type: "scatter", // 散点图
        symbolSize: 20, // 散点的大小
        // x, y 轴的数据
        data: [
          [10.0, 8.04],
          [8.0, 6.95],
          [13.0, 7.58],
          [9.0, 8.81],
          [11.0, 8.33],
          [14.0, 9.96],
          [6.0, 7.24],
          [4.0, 4.26],
          [12.0, 10.84],
          [7.0, 4.82],
          [5.0, 5.68],
        ],
      },
    ],
  });

})
</script>

<template>
  <div ref="myChart" id="scatter1" style="width: 600px; height: 400px"></div>
</template>