<template>
  <!-- <div class="hello"> -->
  <div class="charttest">
    <div
      style="position:realtive;width:580px;height:265px;left:45px;top: 485px;"
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
  name: "BarTwo",
  // props:['BarTwoData'],
  props: {
    BarTwoData: {
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
    bartwoCharts() {
      //var myChart = echarts.init(document.getElementById(this.echarts));
      let myChart = echarts.init(this.$refs.echarts);
      myChart.setOption({
        title: {
          text: "交易场外 ",
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
        color: ["#ffe75f", "#2ad3ff", "#ff6161", "#0d51d5"],
        dataset: {
          source: [
            ["product", "指令笔数", "成交笔数", "委托笔数", "成交金额(亿元)"],
            ["银行间", 16, 9.8, 11.8, 16],
            ["深交所A", 22, 18, 15, 23],
            ["场外", 20, 18, 17, 23.5],
            ["中金所", 22.5, 19.5, 19.5, 29],
            ["上交所A", 16, 11, 13, 16],
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
          },
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
          {
            type: "bar",
            barGap: "0%", //柱图间距
          },
          {
            type: "bar",
            barGap: "0%", //柱图间距
          },
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
    this.bartwoCharts();
  },
  watch: {
    BarTwoData() {
      this.bartwoCharts();
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
