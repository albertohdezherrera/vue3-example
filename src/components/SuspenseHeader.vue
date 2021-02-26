<template>
    <h1>{{ message }}</h1>
</template>

<script>
  export default {
    name: 'SuspenseHeader',
    props: {
      name: String,
    },
    async setup(props) {
      await new Promise(resolve => setTimeout(resolve, 3000));
      return {
          message: `Hola ${props.name}! 👋`
      }
    }
  }
</script>