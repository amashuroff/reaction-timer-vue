<template>
  <p>{{ result }}: {{ score }}ms. {{ quote }}</p>
</template>

<script>
export default {
  name: "Result",
  props: ["score", "isPlaying"],
  data() {
    return {
      quote: null,
      result: "Result",
    };
  },
  mounted() {
    this.showQuote();
  },
  updated() {
    if (this.isPlaying) {
      this.result = "Previos result";
    } else {
      this.result = "Result";
    }
    this.showQuote();
  },
  methods: {
    showQuote() {
      if (this.score >= 350) {
        this.quote = "Slow!!!";
      } else {
        this.quote = "Incredible skills!";
      }
    },
  },
};
</script>

<style></style>
