<template>
  <div>{{ value }}</div>
</template>
<script>
export default {
  name: "random",
  props: {
    fontSize: {
      desc: "字体大小",
      default: "12px",
    },
    color: {
      desc: "字体颜色",
      default: "#000000",
    },
  },
  data: function() {
    return {
      value: Math.floor(((new Date().getTime() / 1000) % 197) + 601),
      styleObj: {
        fontSize: this.fontSize,
        color: this.color,
      },
    };
  },
};
</script>
