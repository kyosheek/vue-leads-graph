<template>
  <div class="auth">
    <h1>LeadHit</h1>
    <AuthForm />
  </div>
</template>

<script>
// @ is an alias to /src
import AuthForm from '@/components/AuthForm.vue';

export default {
  name: 'Auth',
  components: {
    AuthForm,
  },
};
</script>

<style scoped>
.auth {
  max-width: 25vw;
  margin: auto;
}

h1 {
  font-family: Arial, sans-serif;
  font-weight: 800;
  letter-spacing: 1px;
  transform: scale(1.375, 1);
  align-self: flex-start;

  float: left;
  color: #2c3e50;
}
</style>
