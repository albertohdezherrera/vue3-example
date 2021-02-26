<template>
  <h3>{{ allMessage }}</h3>
</template>

<script>
export default {
  data() {
    return {
      message1: 'También sigo siendo',
      message2: 'lo de siempre'
    }
  },
  computed: {
    allMessage: function() {
      return `${this.message1} ${this.message2}`;
    }
  }
}
</script>
