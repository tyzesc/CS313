<template>
  <div class="dot" :style="dotStyle"></div>
  <p class="dot-text" :style="textStyle">{{ position.v }}</p>
</template>

<script>
export default {
  name: "Dot",
  props: {
    position: Object,
  },
  computed: {
    dotStyle() {
      let w = this.position.v / 100;
      let color = 280 - this.position.v;
      return {
        top: this.position.y + "px",
        left: this.position.x + "px",
        transform: "scale(" + w + ")",
        border: `0.1rem solid rgba(0,0,0,0.2)`,
        color: `hsl(${color}, 100%, 50%)`,
        "background-color": `hsl(${color}, 100%, 50%)`,
      };
    },

    textStyle() {
      return {
        top: this.position.y + "px",
        left: this.position.x + "px",
        "font-size": "1rem",
      };
    },
  },
};
</script>

<style>
:root {
  --border-color: red;
}
</style>
<style scoped>
@keyframes shiny {
  from {
    opacity: 1;
    transform: scale(1);
  }
  to {
    opacity: 0;
    transform: scale(5);
  }
}

.dot::after {
  content: "";
  display: block;
  width: 80%;
  height: 80%;
  transform: translate(calc(100%-80% + 1px), calc(100%-80% + 1px));
  border: 1px solid;
  border-radius: 50%;
  animation: shiny 2s infinite;
}

.dot {
  position: absolute;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  transform: translate(-50%, -50%);
}

.dot:hover + .dot-text {
  display: block;
}

.dot-text {
  position: absolute;
  font-weight: bold;
  transform: translate(calc(-25%), calc(-200%));
  transition: all 1s linear;
  text-align: center;
}
</style>