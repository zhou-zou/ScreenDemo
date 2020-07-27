<template>
  <!-- <div class="hello"> -->
  <div class="charttest">
    <div
      style="position: absolute;clear:both;width:580px;height:265px;left:640px;top: 200px;"
      :id="echarts"
      class="echarts"
      ref="echarts"
    ></div>
  </div>
  <!-- </div> -->
</template>

<script>
import echarts from "echarts";

export default {
  name: "BarOne",
  // props:['BarData'],
  props: {
    BarData: {
      type: Array,
      default: () => [],
    },
    legendData: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {};
  },
  methods: {
    baroneCharts() {
      //var myChart = echarts.init(document.getElementById(this.echarts));
      let myChart = echarts.init(this.$refs.echarts);
      myChart.setOption({
        title: {
          text: "交易场内-主动",
          top: "5%",
          left: "40%",
          textStyle: {
            color: "#fff",
            fontStyle: "normal",
            fontWeight: "normal",
            fontFamily: "sans-serif",
            fontSize: 18,
          },
        },
        legend: {
          x: "center",
          y: "bottom",
          icon: "circle",
          textStyle: {
            color: "#fff",
          },
        },
        tooltip: {},
        color: ["#ffe75f", "#2ad3ff", "#ff6161", "#0d51d5", "#935ee5"],
        dataset: {
          source: [
            [
              "product",
              "指令笔数",
              "成交笔数",
              "委托笔数",
              "成交金额(百万元)",
              "净买入金额(百万元)",
            ],
            ["港股通(深)", 16, 9.8, 13, 16, 27],
            ["港股通(沪)", 16, 9.8, 13, 16, 27],
            ["深交所A", 22, 18, 16, 23, 14],
            ["上交所", 23, 16, 20, 29, 13],
          ],
        },
        xAxis: {
          type: "category",
          axisLabel: {
            textStyle: {
              color: "#b1ddff",
            },
          },
          axisLine: {
            lineStyle: {
              color: "#b1ddff",
            },
          }
        },
        yAxis: {
          type: "value",
          min: 0,
          max: 30,
          interval: Math.ceil(30 / 3),
          axisLabel: {
            formatter: "{value}k",
            textStyle: {
              color: "#b1ddff",
            },
          },
          splitLine: {
            show: false,
          },
          axisLine: {
            lineStyle: {
              color: "#b1ddff",
            },
          },
        },
        // Declare several bar series, each will be mapped
        // to a column of dataset.source by default.
        series: [
          { type: "bar" ,
            barGap:'0%',//柱图间距
          },
          { type: "bar" },
          { type: "bar" },
          { type: "bar" },
          { type: "bar" },
        ],
      });
    },
  },
  computed: {
    echarts() {
      return "echarts" + Math.random() * 100000;
    },
  },
  mounted() {
    this.baroneCharts();
  },
  watch: {
    BarData() {
      this.baroneCharts();
    },
  },
  components: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.echarts {
  position: absolute;
  top: 193px;
  left: 95px;
  z-index: 100;
}
</style>
