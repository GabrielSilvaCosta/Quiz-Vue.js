<template>
    <div class="result">
      <div class="title">{{ results[resultIndex].title }}</div>
      <div class="desc">{{ results[resultIndex].desc }}</div>
      <button type="button" class="reset-btn" @click="reset">Reset</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ["results", "totalCorrect"],
    computed: {
      resultIndex() {
        let index = 0;
        
        this.results.forEach((result, i) => {
          if (this.totalCorrect >= result.min && this.totalCorrect <= result.max) {
            index = i;
          }
        });
        return index;
      }
    },
    methods: {
      reset() {
        this.$emit("reset");
      }
    }
  };
  </script>
  
  <style></style>
  