<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <span>click me</span>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      //   console.log(this.delay);
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      //   console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
  //   updated() {
  //     console.log("component updated");
  //   },
  //   unmounted() {
  //     console.log("component unmounted");
  //     // usefull for routing
  //   },
};
</script>

<style>
.block {
  width: 15rem;
  height: 15rem;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 3rem auto;
  padding: 1rem;
  text-align: center;
  border-radius: 10px;
  color: #fff;
  background-color: rgb(13, 124, 197);
}
</style>