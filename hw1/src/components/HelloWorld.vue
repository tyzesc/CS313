<template>
  <div class="hello">
    <img ref="yzuImg" id="yzuImg" src="../assets/yzu.jpg" />
    <Dot v-for="dot in computedDots" :key="dot" :position="dot" />
  </div>
</template>

<script>
import Dot from "./Dot";
export default {
  name: "HelloWorld",

  components: {
    Dot,
  },

  data() {
    return {
      dots: [
        // 一館
        { x: 328, y: 305, v: Math.floor(Math.random() * 200 + 80) },
        { x: 328, y: 270, v: Math.floor(Math.random() * 200 + 80) },
        { x: 328, y: 235, v: Math.floor(Math.random() * 200 + 80) },
        // 6
        { x: 302, y: 206, v: Math.floor(Math.random() * 200 + 80) },
        { x: 302, y: 175, v: Math.floor(Math.random() * 200 + 80) },
        { x: 300, y: 141, v: Math.floor(Math.random() * 200 + 80) },
        // 5
        { x: 340, y: 137, v: Math.floor(Math.random() * 200 + 80) },
        { x: 360, y: 110, v: Math.floor(Math.random() * 200 + 80) },
        { x: 396, y: 136, v: Math.floor(Math.random() * 200 + 80) },
        // 2
        { x: 447, y: 136, v: Math.floor(Math.random() * 200 + 80) },
        // 3
        { x: 445, y: 235, v: Math.floor(Math.random() * 200 + 80) },
        { x: 445, y: 279, v: Math.floor(Math.random() * 200 + 80) },
        // 7
        { x: 507, y: 250, v: Math.floor(Math.random() * 200 + 80) },
        { x: 504, y: 283, v: Math.floor(Math.random() * 200 + 80) },
        // 男宿
        { x: 737, y: 109, v: Math.floor(Math.random() * 200 + 80) },
        // 活動中心
        { x: 734, y: 173, v: Math.floor(Math.random() * 200 + 80) },
        // 體育館
        { x: 721, y: 216, v: Math.floor(Math.random() * 200 + 80) },
      ],
      clientWidth: 920,
      clientHeight: 631,
      originWidth: 920,
      originHeight: 631,
    };
  },

  computed: {
    computedDots: function () {
      return JSON.parse(JSON.stringify(this.dots)).map((d) => {
        d.x *=
          this.clientWidth /
          (this.originWidth === 0 ? this.clientWidth : this.originWidth);
        d.y *=
          this.clientHeight /
          (this.originHeight === 0 ? this.clientHeight : this.originHeight);
        return d;
      });
    },
  },

  mounted() {
    const fitWindow = () => {
      this.clientWidth = this.$refs.yzuImg.clientWidth;
      this.clientHeight = this.$refs.yzuImg.clientHeight;
    };
    window.addEventListener("load", fitWindow);
    window.addEventListener("resize", fitWindow);
  },
};
</script>

<style scoped>
.hello {
  width: 100vw;
  max-width: 100%;
  height: auto;
}

img {
  width: 100%;
  filter: grayscale();
  opacity: 0.5;
}
</style>
