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
      subtext: "Grid网格柱状图",
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
    grid: {
      // 控制网格的上下左右距离
      left: "20%",
      top: "10%",
      right: "20%",
      bottom: "20%",
      containLabel: true, // 包含坐标轴的刻度标签
      show: true, // 显示网格
      backgroundColor: "rgba(128, 128, 128, 0.1)", // 网格背景颜色
      tootip: {
        show: true,
        trigger: "axis",
        axisPointer: {
          type: "cross",
          label: {
            backgroundColor: "#6a7985",
          },
        },
      },
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "日期",
        type: "bar", // 系列类别
        data: [150, 230, 224, 218, 135, 147, 260], // 对应 y 轴的数据
        // 最大值和最小值
        markPoint: {
          data: [
            { type: "max", name: "最大值" },
            { type: "min", name: "最小值" },
          ],
        },
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="bar1" style="width: 600px; height: 400px"></div>
</template>
