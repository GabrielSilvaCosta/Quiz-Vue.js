<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <Questions
        v-if="questionsAnswered <= questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        :currentQuestion="currentQuestion"
        @question-answered="questionAnswered"
      />
      <Result
        v-else
        :results="results"
        :totalCorrect="totalCorrect"
        @reset="reset"
      />
    </transition>
  </div>
</template>

<script>
import Result from "./components/Result.vue";
import Questions from "./components/Questions.vue";
export default {
  name: "App",
  components: {
    Result,
    Questions,
  },
  data() {
    return {
      questionsAnswered: 1,
      totalCorrect: 0,
      currentQuestion: 1,
      questions: [
        {
          q: "Qual é a capital do Brasil?",
          answers: [
            { text: "São Paulo", is_correct: false },
            { text: "Rio de Janeiro", is_correct: false },
            { text: "Brasília", is_correct: true },
            { text: "Salvador", is_correct: false },
          ],
        },
        {
          q: "Qual é o maior planeta do Sistema Solar?",
          answers: [
            { text: "Terra", is_correct: false },
            { text: "Júpiter", is_correct: true },
            { text: "Saturno", is_correct: false },
            { text: "Marte", is_correct: false },
          ],
        },
        {
          q: "Qual é o maior oceano do mundo?",
          answers: [
            { text: "Atlântico", is_correct: false },
            { text: "Índico", is_correct: false },
            { text: "Pacífico", is_correct: true },
            { text: "Artico", is_correct: false },
          ],
        },
        {
          q: "Qual é a capital da França?",
          answers: [
            { text: "Berlim", is_correct: false },
            { text: "Roma", is_correct: false },
            { text: "Londres", is_correct: false },
            { text: "Paris", is_correct: true },
          ],
        },

        {
          q: "Qual é a fórmula química da água?",
          answers: [
            { text: "CO2", is_correct: false },
            { text: "H2O", is_correct: true },
            { text: "NaCl", is_correct: false },
            { text: "C6H12O6", is_correct: false },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Tenta de novo!",
          desc: "Estude mais um pouco e tente novamente!",
        },
        {
          min: 5,
          max: 5,
          title: "Parabéns, voce acertou!",
          desc: "Mandou bem, os estudos estão concluídos!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
      this.currentQuestion++;
    },
    reset() {
      this.questionsAnswered = 1;
      this.totalCorrect = 0;
      this.currentQuestion = 1;
    },
  },
};
</script>

<style></style>
