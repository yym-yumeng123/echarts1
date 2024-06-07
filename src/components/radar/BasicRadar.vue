<!-- 雷达图 -->

<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "雷达图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    tooltip: {},
    legend: {
      left: "left",
      top: 40,
      orient: "vertical",
      data: ["预算分配", "实际开销"],
    },
    // 雷达图的指示器, 用来指定雷达图中的多个变量
    radar: {
      shape: "circle", // 雷达图绘制类型 polygon | circle | rect | roundedRect | sector | ring
      // 雷达图的指示器, 用来指定雷达图中的多个变量
      indicator: [
        { name: "销售", max: 6500 },
        { name: "管理", max: 16000 },
        { name: "信息技术", max: 30000 },
        { name: "客服", max: 38000 },
        { name: "研发", max: 52000 },
        { name: "市场", max: 25000 },
      ],
      // 半径
      radius: 120,
      // 坐标系旋转角度, 支持角度和弧度
      startAngle: 90,
      splitNumber: 6,
      // 雷达图的分割区域
      splitArea: {
        areaStyle: {
          color: ["rgba(255, 0, 0, 0.5)", "rgba(0, 255, 0, 0.5)"],
          shadowColor: "rgba(0, 0, 0, 0.5)",
        },
      },
    },
    series: [
      {
        name: "预算 vs 开销",
        type: "radar",
        data: [
          {
            value: [4300, 10000, 28000, 35000, 50000, 19000],
            name: "预算分配",
            lineStyle: {
              color: "red",
              type: "dashed",
            },
            areaStyle: {
              color: "rgba(255, 0, 0, 0.5)",
            },
          },
          {
            value: [5000, 14000, 28000, 31000, 42000, 21000],
            name: "实际开销",
          },
        ],
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="radar1" style="width: 600px; height: 400px"></div>
</template>