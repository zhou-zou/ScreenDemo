<template>
  <!-- <div class="hello"> -->
  <div class="charttest">
    <div
      style="position:realtive;clear:both;width:580px;height:265px;left:45px;top: 200px;"
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
  name: "HelloWorld",
  // props:['chartData'],
  props: {
    chartData: {
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
    drawCharts() {
      //var myChart = echarts.init(document.getElementById(this.echarts));
      let myChart = echarts.init(this.$refs.echarts);
      myChart.setOption({
        title: [
          {
            text: "各市场委托笔数占比",
            top: "5%",
            left: "10%",
            textStyle: {
              color: "#ffffff",
              fontStyle: "normal",
              fontWeight: "normal",
              fontFamily: "sans-serif",
              fontSize: 18,
            },
          },
          {
            text: "各市场成交笔数占比",
            top: "5%",
            left: "60%",
            textStyle: {
              color: "#ffffff",
              fontStyle: "normal",
              fontWeight: "normal",
              fontFamily: "sans-serif",
              fontSize: 18,
            },
          },
        ],
        color: [
          "#4BF26F",
          "#FFE567",
          "#F19D3A",
          "#FF5969",
          "#935EE5",
          "#1059D2",
          "#24CFFF",
        ],
        legend: {
          x: "center",
          y: "bottom",
          icon: "circle",
          textStyle: {
            color: "white",
          },
        },
        tooltip: {},
        dataset: {
          source: [
            ["product", "2012", "2013", "2014", "2015", "2016", "2017", "2018"],
            ["场外", 0.18, 0.18, 69.2, 72.4],
            ["上交所A", 0.12, 0.12, 79.5, 86.4],
            ["中金所", 0.07, 0.07, 69.2, 72.4],
            ["银行间", 0.05, 0.05, 69.2, 72.4],
            ["港股通(沪)", 0.04, 0.04, 65.1, 53.3],
            ["深交所A", 0.3, 0.3, 69.2, 72.4],
            ["港股通(深)", 0.2, 0.2, 85.7, 83.1],
          ],
        },
        series: [
          {
            type: "pie",
            radius: 60,
            center: ["25%", "50%"],
            label: {
              normal: {
                //position: 'inner'
                formatter: "{d}%",
                color: "white",
              },
            },
            labelLine: {
              normal: {
                show: false,
              },
            },
          },
          {
            type: "pie",
            radius: 60,
            center: ["75%", "50%"],
            encode: {
              itemName: "product",
              value: "2013",
            },
            label: {
              normal: {
                //position: 'inner'
                formatter: "{d}%",
                color: "white",
              },
            },
            labelLine: {
              normal: {
                show: false,
              },
            },
          },
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
    this.drawCharts();
  },
  watch: {
    chartData() {
      this.drawCharts();
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
