<!-- 中国地图 -->
<script setup>
// 中国地图json 数据
import mapJson from "../../assets/map.json";
// 安徽地图json 数据
import anhuiJson from "../../assets/anhui.json";
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 中国地图 注册地图 json
  echarts.registerMap("china", mapJson);
  myEcharts.setOption({
    title: {
      text: "ECharts 入门示例",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
      subtext: "中国地图",
    },
    tooltip: {
      trigger: "item",
      formatter: "{b}<br/>{c}",
    },
    // 地理坐标系组件
    geo: {
      type: "map",
      map: "china",
      roam: true, // 开启缩放和平移
      zoom: 1.2, // 缩放比例
      // center: [104.114129, 37.550339], // 中心点
      label: {
        show: true,
        color: "rgba(0,0,0,0.4)",
      },
      itemStyle: {
        borderColor: "rgba(0, 0, 0, 0.2)",
      },
      emphasis: {
        areaColor: null,
        shadowOffsetX: 0,
        shadowOffsetY: 0,
        shadowBlur: 20,
        borderWidth: 0,
        shadowColor: "rgba(0, 0, 0, 0.5)",
      },
    },
    series: [
      // 散点图
      {
        type: "scatter",
        coordinateSystem: "geo",
        data: [
          // 坐标点 [经度, 纬度, 值]
          { name: "北京", value: [116.46, 39.92, 100] },
          { name: "广州", value: [113.23, 23.16, 100] },
          { name: "深圳", value: [114.07, 22.62, 100] },
          { name: "重庆", value: [106.54, 29.59, 100] },
          { name: "天津", value: [117.2, 39.13, 100] },
          { name: "成都", value: [104.06, 30.67, 100] },
          { name: "南京", value: [118.78, 32.04, 100] },
          { name: "武汉", value: [114.31, 30.52, 100] },
          { name: "西安", value: [108.95, 34.27, 100] },
          { name: "郑州", value: [113.65, 34.76, 100] },
          { name: "长沙", value: [113, 28.21, 100] },
          { name: "沈阳", value: [123.38, 41.8, 100] },
          { name: "哈尔滨", value: [126.63, 45.75, 100] },
          { name: "太原", value: [112.53, 37.87, 100] },
          { name: "西宁", value: [101.74, 36.56, 100] },
          { name: "兰州", value: [103.73, 36.03, 100] },
          { name: "银川", value: [106.27, 38.47, 100] },
        ],
        coordinateSystem: "geo", // 坐标系设置
        symbolSize: 20, // 散点的大小
        label: {
          show: true,
          formatter: "{b}",
        },
      },
      {
        type: "effectScatter", // 涟漪效果散点图
        coordinateSystem: "geo",
        data: [
          // 坐标点 [经度, 纬度, 值]
          { name: "上海", value: [121.48, 31.22, 100] },
        ],
        // 设置涟漪效果
        rippleEffect: {
          number: 5, // 涟漪的数量
          brushType: "stroke",
          scale: 5, // 涟漪的大小
        },
        itemStyle: {
          color: "red",
        },
      },
    ],
  });
});
</script>

<template>
  <div>
    <div ref="myChart" id="map" style="width: 100%; height: 600px"></div>
  </div>
</template>