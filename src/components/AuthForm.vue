<template>
  <h1>{{ title }}</h1>
  <form>
    <label for="id">ID сайта:<input id="id" type="text"></label>
    <button>Войти</button>
  </form>
</template>

<script>
export default {
  name: 'AuthForm',
  props: {
    title: String,
  },
};
</script>

<style scoped>

</style>
