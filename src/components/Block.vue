<template>
  <div class="block" v-if="showBlocks" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlocks: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("componemt mounted");
    setTimeout(() => {
      this.showBlocks = true;
      this.startTimer();
      console.log(this.delay);
    }, this.delay);
  },
  // See the Vue hooks life cycle
  updated() {
    console.log("component updated");
  },
  unmounted() {
    console.log("unmounted");
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
