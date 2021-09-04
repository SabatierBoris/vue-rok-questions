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
      <Question v-for="(question, i) in results" :question="question.item.question" :answers="question.item.good_answers" :matches="question.matches" :key="i" />
    </div>
  </div>
</template>

<script>
import VueFuse from 'vue-fuse'
import axios from 'axios'
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
        minMatchCharLength: 3,
        findAllMatches: false,
      },
      questions: [],
    };
  },
  methods: {
    handleResults (r) {
      this.results = r
    },
  },
  created() {
    axios
      .get('rok_questions_db.json')
      .then(response => (this.questions = response.data))
  }
}
</script>

<style lang="scss">
  @import "./scss/main.scss";
</style>
