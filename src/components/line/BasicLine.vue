<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "折线图/曲线图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    legend: {
    },
    tooltip: {
      trigger: "axis",
    },
    xAxis: {
      type: "category",
      data: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
    },
    yAxis: {
      type: "value",
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "访问来源",
        type: "line", // 折线图
        data: [150, 230, 224, 218, 135, 147, 260],
        smooth: true, // 平滑曲线
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgba(128, 255, 165)",
            },
            {
              offset: 1,
              color: "rgba(1, 191, 236)",
            },
          ]),
        }, // 区域填充
        markPoint: {
          data: [
            { type: "max", name: "最大值" },
            { type: "min", name: "最小值" },
          ],
        },
        markLine: {
          data: [{ type: "average", name: "平均值" }],
        },
      },
    ],
  });
  // 监听窗口变化
  window.addEventListener("resize", () => {
    myEcharts.resize();
  });
});
</script>

<template>
  <div ref="myChart" id="line1" style="width: 100%; height: 400px"></div>
</template>
