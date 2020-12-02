<template>
  <div class="block" v-if="showBlock" v-on:click="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
    console.log(`Component Mounted ${this.delay}`);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: rgb(2, 230, 154);
  color: rgb(255, 255, 255);
  text-align: center;
  margin: 10px auto;
  padding: 100px 0;
  cursor: pointer;
}
</style>
