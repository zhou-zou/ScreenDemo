<template>
  <div id="app">
    <p class="south">南方基金大屏</p>
    <div class="time">
      {{ nowDate }}
    </div>
    <div class="picture">
      <img src="./images/南方基金大屏v背景图.jpg" />
    </div>
    <HelloWorld :chartData="chartData" />
    <BarOne :BarData="BarData" />
    <BarTwo :BarTwoData="BarTwoData" />
    <BarThree :BarThreeData="BarThreeData" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import BarOne from "./components/BarOne";
import BarTwo from "./components/BarTwo";
import BarThree from "./components/BarThree";

let moment = require("moment");

export default {
  name: "App",
  mounted() {},
  components: {
    HelloWorld,
    BarOne,
    BarTwo,
    BarThree,
  },
  data() {
    return {
      chartData: [],
      BarData: [],
      BarTwoData: [],
      BarThreeData: [],
      nowDate: new Date().getTime(), //获取时间
      value: '',
      // datas: {
      //   chartData: [
      //     { value: 5, name: "衬衫" },
      //     { value: 20, name: "羊毛衫" },
      //     { value: 36, name: "雪纺衫" },
      //     { value: 10, name: "裤子" },
      //     { value: 10, name: "高跟鞋" },
      //     { value: 20, name: "袜子" },
      //   ],
      // },

      // chartData: [],
      // legendData: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
    };
  },
  // created() {
  //   this.nowDate = moment(this.nowDate).format("YYYY-MM-DD HH:mm:ss");
  // },
  methods: {},
 destroyed() {
    clearInterval(value)
  },
  created() {
    let value = setInterval(() => {
      this.nowDate = moment().format("YYYY-MM-DD HH:mm:ss");
    }, 1000);
  },
  // mounted() {
  //   this.nowDate() = setInterval(this.get, 1000);
  // }
  // created() {
  //   getPieData().then((res) => {
  //     console.log(res);
  //     this.chartData = res.data.list;
  //   });
  // },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  /* position: relative; */
  /* background-image: url(''); */
}
.picture {
  position: relative;
}
img {
  width: 1200px;
  height: 650px;
  position: relative;
  clear: both;
}
.south {
  position: relative;
  /* left: 709px; */
  background-image: linear-gradient(to bottom, white, dodgerblue);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-size: 25px;
  font-weight: bold;
  font-stretch: normal;

  clear: both;
  top: 82px;
  z-index: 100;
  text-align: center;
  letter-spacing: 3px;
}
.time {
  position: relative;
  clear: both;
  width: 280px;
  height: 20px;
  top: 38px;
  right: -945px;
  z-index: 100;
  color: #92edfe;
  font-size: 20px;
  z-index: 100;
}
</style>
