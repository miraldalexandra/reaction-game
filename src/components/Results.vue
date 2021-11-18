<template>
  <p>reaction time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 400) {
      this.rank = "rapid reflection";
    } else {
      this.rank = "snail pace...";
    }
  },
};
</script>

<style>
.rank {
  color: rgb(36, 35, 35);
  font-size: 1.3em;
  font-weight: bold;
}
</style>