<template>
  <div class="block" @click="stopTimer" v-if="showBlock">Click me</div>
</template>

<script>
export default {
  props: ["delay"],
  name: "Block",
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
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
      this.$emit("reacted", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background-color: #0faf87;
  color: white;
  text-transform: uppercase;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
