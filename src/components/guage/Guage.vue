<!-- 仪表盘 -->

<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 仪表盘
  myEcharts.setOption({
    title: {
      text: "仪表盘",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    tooltip: {
      formatter: "{a} <br/>{b} : {c}%",
    },
    series: [
      {
        name: "业务指标",
        type: "gauge",
        detail: { formatter: "{value}%", valueAnimation: true },
        progress: { show: true, roundCap: true },
        data: [{ value: 50, name: "完成率" }],
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="guage" style="width: 600px; height: 400px"></div>
</template>