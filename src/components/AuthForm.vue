<template>
  <form
    id="authForm"
    @submit.prevent="processForm">
      <label for="id">ID сайта:
      <input
        id="id"
        type="text"
        v-model="inputId">
      </label>
      <button>Войти</button>
  </form>
  <div class="errorMsgWrapper">
    <p>{{ errorMsg }}</p>
  </div>
</template>

<script>
export default {
  name: 'AuthForm',
  el: '#authForm',
  data() {
    return {
      inputId: '',
      error: false,
      errorMsg: '',
    };
  },
  methods: {
    processForm() {
      if (this.inputId.length !== 24) {
        this.error = true;
        this.errorMsg = 'id сайта должен содержать 24 символа';
      } else {
        let xhr = new XMLHttpRequest();
        xhr.open("GET", "https://track-api.leadhit.io/client/test_auth", true);
        xhr.setRequestHeader('Api-Key', '5f8475902b0be670555f1bb3:eEZn8u05G3bzRpdL7RiHCvrYAYo');
        xhr.setRequestHeader('Leadhit-Site-Id', this.inputId);
        xhr.send();

        xhr.onload = (e) => { // eslint-disable-line no-unused-vars
          if (xhr.readyState === 4) {
            if (xhr.status === 200) {
              localStorage.setItem('leadhit-site-id', this.inputId);
              this.$router.push('/analytics');
            } else {
              console.log('status is not 200')
              this.error = true;
              this.errorMsg = 'Ошибка при обработке запроса';
            }
          }
        };
        xhr.onerror = (e) => { // eslint-disable-line no-unused-vars
          this.error = true;
          this.errorMsg = 'Ошибка на стороне клиента';
        };
      }
    },
  },
  watch: {
    inputId: function(newInputId, oldInputId) { // eslint-disable-line no-unused-vars
      if (this.error) {
        this.error = false;
        this.errorMsg = '';
      }
    },
  },
};
</script>

<style scoped>

</style>
