<!-- 数据集的使用 -->
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
      subtext: "数据集的使用",
    },
    tooltip: {},
    dataset: [
      {
        // 数据的来源
        source: [
          ["product", "2015", "2016", "2017"],
          ["Matcha Latte", 43.3, 85.8, 93.7],
          ["Milk Tea", 83.1, 73.4, 55.1],
          ["Cheese Cocoa", 86.4, 65.2, 82.5],
          ["Walnut Brownie", 72.4, 53.9, 39.1],
        ],
        // 数据的分类
        dimensions: ["product", "2015", "2016", "2017"],
      },
      {
        // 数据的转换
        transform: {
          type: "sort", // 排序
          config: { dimension: "2015", order: "desc" }, // 降序
        },
      },
    ],
    xAxis: { type: "category", axisLabel: { rotate: 45, interval: 0 } },
    yAxis: {},
    series: [
      {
        type: "bar",
        // 数据的映射 2015 -> 2016 -> 2017
        // x 轴: product y 轴: 2015
        encode: { x: "product", y: "2015" },
      },
      {
        type: "bar",
        encode: { x: "product", y: "2016" },
      },
      {
        type: "bar",
        encode: { x: "product", y: "2017" },
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" style="width: 100%; height: 600px"></div>
</template>