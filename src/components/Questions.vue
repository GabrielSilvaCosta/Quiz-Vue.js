<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(questionsAnswered / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ questionsAnswered }} de  {{ questions.length }} perguntas
      </div>
    </div>
    <transition-group name="fade">
      <div class="single-question" v-if="currentQuestion !== null">
        <div class="question">{{ questions[currentQuestion - 1].q }}</div>
        <div class="answers">
          <div
            class="answer"
            v-for="(answer, j) in questions[currentQuestion - 1].answers"
            :key="j"
            @click.prevent="selectAnswer(answer.is_correct)"
          >
            {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ["questions", "questionsAnswered", "currentQuestion"],
  emits: ["question-answered"],
  methods: {
    selectAnswer(is_correct) {
      this.$emit("question-answered", is_correct);
    },
  },
};
</script>

<style></style>
