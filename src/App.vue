<template>
  <div class="container">
    <div class="tile is-ancestor is-vertical">
      <div class="tile is-child box field has-addons">
        <p class="control">
          <span class="select">
            <select>
              <option>Français</option>
            </select>
          </span>
        </p>
        <p class="control is-expanded has-icons-left">
          <VueFuse :fuse-opts="options" :list="questions" :defaultAll="true" @fuse-results="handleResults" class="input" autofocus/>
          <span class="icon is-small is-left">
            <i class="fas fa-search"></i>
          </span>
        </p>
        <p class="control">
          <a class="button is-static">{{ results.length }} questions</a>
        </p>
      </div>
      <Question v-for="(question, i) in results" :data="question" :key="i" />
    </div>
  </div>
</template>

<script>
import VueFuse from 'vue-fuse'
import Question from './components/Question.vue'

export default {
  name: 'App',
  components: {
    VueFuse,
    Question,
  },
  data () {
    return {
      results: [],
      options: {
        keys: [
          {
            name: 'question',
            weight: 2,
          },
          'good_answers',
        ],
        includeScore: true,
        includeMatches: true,
        minMatchCharLength: 2,
      },
      questions: [{
        question: "Raphaël est principalement connu pour laquelle des œuvres suivantes ?",
        good_answers: [
          "L'École d'Athènes"
        ],
        bad_answers: [
          "La Cène",
          "Les décorations murales de la Chapelle Sixtine",
          "Mona Lisa"
        ],
      }, {
        question: "Quel commandant était considéré comme un ennemi de Rome depuis ses jeunes jours ?",
        good_answers: [
          "Hannibal Barca"
        ],
        bad_answers: [
          "Särka",
          "Frédéric 1er",
          "Boadicée",
          "Sârka",
          "Frédéric ler",
          "Séärka",
          "Sérka"
        ],
      }, {
        question: "Combien de phases compose l’événement Le plus grand gouverneur ?",
        good_answers: ["6"],
        bad_answers: [
          "7",
          "4"
        ],
      }]
    };
  },
  methods: {
    handleResults (r) {
      this.results = r
    },
  },
}
</script>

<style lang="scss">
  @import "./scss/main.scss";
</style>
