<template>
  <div class="tile is-child box">
    <p class="title">{{ data.item.question }}</p>
    <p>{{ data.item.good_answers.join(', ') }}</p>
  </div>
</template>

<script>
export default {
  name: 'Question',
  props: {
    data: Object
  }
}
</script>
