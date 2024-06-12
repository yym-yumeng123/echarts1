<!-- 中国地图 -->
<script setup>
// 中国地图json 数据
import mapJson from '../../assets/map.json'
// 安徽地图json 数据
import anhuiJson from '../../assets/anhui.json'
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 中国地图 注册地图 json
  echarts.registerMap("china", anhuiJson);
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
        normal: {
          show: true,
          textStyle: {
            color: "rgba(0,0,0,0.4)",
          },
        },
      },
      itemStyle: {
        normal: {
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
    },
  });
});
</script>

<template>
  <div>
    <div ref="myChart" id="map" style="width: 100%; height: 600px;"></div>
  </div>
</template>