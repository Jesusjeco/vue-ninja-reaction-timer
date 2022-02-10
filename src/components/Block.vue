<template>
  <div class="block" v-if="showBlock" @click="stopTimer">{{ blockText }}</div>
</template>

<script>
  export default {
    props: ["delay"],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0,
        blockText: "click me! QUICK!",
      };
    },
    methods: {
      startTimer() {
        this.reactionTime = 0;
        this.timer = setInterval(() => {
          this.reactionTime += 10;
        }, 10);
      },
      stopTimer() {
        clearInterval(this.timer);
        console.log("timer stop at " + this.reactionTime + " ms");
        this.blockText = "Your time is: " + this.reactionTime;

        this.$emit('timerStop',this.reactionTime);
      },
    },
    mounted() {
      console.log("Block component mounted");

      setTimeout(() => {
        this.showBlock = true;

        console.log("Timeout finish");
        console.log("time waited " + this.delay);
        this.startTimer();
      }, this.delay);
    },
    updated() {
      console.log("Block component updated");

      console.log("Delay: " + this.delay);
    },
    unmounted() {
      console.log("Block component unmounted");
    },
  };
</script>

<style scoped>
  .block {
    width: 400px;
    background-color: aqua;
    border-radius: 20px;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>
