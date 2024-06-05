<script setup>
import * as echarts from "echarts";
import { onMounted } from "vue";

onMounted(() => {
  const myEcharts = echarts.init(document.getElementById("main"));
  myEcharts.setOption({
    title: {
      text: "ECharts 入门示例",
    },
    tooltip: {},
    xAxis: {
      data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
    },
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
  <div id="main" style="width: 600px; height: 400px"></div>
</template>

<style scoped>
</style>
