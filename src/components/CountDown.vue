<template>
  <div class="count-down" :style="styleObj">
    {{ countResult }}
  </div>
</template>
<script>
export default {
  props: {
    range: {
      desc: "时间范围(秒)",
      default: 4,
    },
    steps: {
      desc: "时间跨度",
      default: 100,
    },
    color: {
      desc: "字体颜色",
      default: "#000",
    },
    size: {
      desc: "字体大小",
      default: "12px",
    },
  },
  name: "count-down",
  data: function() {
    return {
      countResult: "--:--:--",
      styleObj: {
        fontSize: this.size,
        color: this.color,
      },
    };
  },
  created() {
    var ms = +this.range * 60 * 1000; // 4 分钟
    let interval = +this.steps;
    var self = this;
    var mstimer = setInterval(function() {
      let m = Math.floor(ms / (60 * 1000));
      let smr = Math.floor(ms - m * 60 * 1000) / 1000 + "";
      let result = smr.split(".");
      let ss = +result[0];
      let mm = +(result[1] || "0");
      ms = ms - interval;
      self.countResult = `${m < 10 ? "0" + m : m}:${
        ss < 10 ? "0" + ss : ss
      }:${mm}`;

      if (m == 0 && +smr == 0) {
        clearInterval(mstimer);
      }
    }, interval);
  },
};
</script>
<style>
.count-down {
  text-align: center;
  padding-left: 20px;
}
</style>
