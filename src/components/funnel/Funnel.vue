<!-- 漏斗图 -->

<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 漏斗图
  myEcharts.setOption({
    title: {
      text: "漏斗图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    tooltip: {
      trigger: "item",
      formatter: "{a} <br/>{b} : {c}%",
    },
    legend: {
      data: ["展现", "点击", "访问", "咨询", "订单"],
    },
    series: [
      {
        name: "预期",
        type: "funnel",
        left: "10%", // 距离左边的距离
        width: "80%", // 宽度
        label: { // 标签
          position: "inside",
          formatter: "{b} {c}%",
        },
        labelLine: { // 标签线
          show: false,
        },
        itemStyle: {
          opacity: 0.7,
        },
        emphasis: {
          label: {
            fontSize: 20,
          },
        },
        data: [
          { value: 60, name: "访问" },
          { value: 40, name: "咨询" },
          { value: 20, name: "订单" },
          { value: 80, name: "点击" },
          { value: 100, name: "展现" },
        ],
        sort: "ascending", // 排序 ascending | descending | none
        itemStyle: {
          borderColor: "#fff",
          borderWidth: 1,
        },
      },
    ],
  });
});

</script>

<template>
  <div ref="myChart" id="funnel" style="width: 100%; height: 500px;"></div>
</template>