<template>
  <h1>LeadHit</h1>
  <div class="auth">
    <AuthForm title="LeadHit"/>
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
