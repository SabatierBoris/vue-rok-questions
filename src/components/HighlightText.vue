<template>
  <span v-html="reversedMessage"></span>
</template>

<script>
export default {
  name: 'HighlightText',
  props: {
    text: {
      type: String,
      required: true
    },
    indices: {
      type: Array,
      required: true
    },
  },
  computed: {
    reversedMessage: function () {
      var currentPos = 0;
      var output = [];
      for (const i in this.indices) {
        const indice = this.indices[i];
        if(indice[0] < currentPos) {
          continue;
        }
        output.push(this.text.substring(currentPos, indice[0]));
        output.push('<span class="has-text-danger">');
        output.push(this.text.substring(indice[0], indice[1]+1));
        output.push('</span>');
        currentPos = indice[1]+1;
      }

      output.push(this.text.substring(currentPos));
      return output.join('');
    }
  },
}
</script>
