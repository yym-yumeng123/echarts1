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
      subtext: "水平柱状图",
    },
    // x 轴 參數
    xAxis: {
      type: "value",
    },
    yAxis: {
      // 坐标轴类型: 类目轴
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    tootip: {},
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "日期",
        type: "bar", // 系列类别
        data: [150, 230, 224, 218, 135, 147, 260], // 对应 y 轴的数据
        barWidth: 20,
        itemStyle: {
          normal: {
            color(params) {
              const colorList = [
                "#C1232B",
                "#B5C334",
                "#FCCE10",
                "#E87C25",
                "#27727B",
                "#FE8463",
                "#9BCA63",
              ];
              return colorList[params.dataIndex];
            },
            label: {
              show: true,
              position: "right",
              textStyle: {
                color: "black",
              },
            },
          },
        },
        // 最大值和最小值
        markPoint: {
          data: [
            { type: "max", name: "最大值", valueIndex: 0 },
            { type: "min", name: "最小值" },
          ],
        },
        markLine: {
          data: [
            {
              name: "平均值",
              type: "average",
              // valueIndex: 0,
              // symbol: "pin",
              // symbolSize: 50,
              // symbolRotate: 0,
              // symbolOffset: [0, 0],
              itemStyle: {
                color: "red",
                borderColor: "blue",
                borderWidth: 1,
                borderType: "solid",
                shadowBlur: 10,
                shadowColor: "black",
                shadowOffsetX: 5,
                shadowOffsetY: 5,
                opacity: 1,
              },
            },
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
