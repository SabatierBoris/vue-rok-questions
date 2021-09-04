<template>
  <div class="tile is-child box">
    <p class="title"><HighlightText :text="question" :indices="getIndices('question', question)" /></p>

    <HighlightText v-for="(answer, i) in answers" :text="answer" :indices="getIndices('good_answers', answer)" :key="i" />
  </div>
</template>

<script>
import HighlightText from './HighlightText.vue'

export default {
  name: 'Question',
  props: {
    question: {
      type: String,
      required: true,
    },
    answers: {
      type: Array,
      required: true,
    },
    matches: {
      type: Array,
    },
  },
  methods: {
    getIndices: function (key, value) {
      if (this.matches === undefined) {
        return [];
      }

      const  matches = this.matches.filter(match => match.key === key && match.value === value);
      if (matches.length === 0) {
        return [];
      }

      return matches[0].indices;
    }
  },
  components: {
    HighlightText,
  },
}
</script>
