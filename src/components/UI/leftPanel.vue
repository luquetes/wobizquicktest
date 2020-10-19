<template>
    <div class="box vh-100 white-bg box-shadow">
        <div class="row h-100">
        <div class="h-100 col">
            <a href="https://www.wobiz.com/">
            <img src="@/assets/descarga.png" alt="" class="logo">
            </a>
            <h2 class="greenish-blue-text mt-5 mb-4 bolder">Ingresa a tu cuenta</h2>
            <Form @onFormSubmitted="submittedForm" />
        </div>
        </div>
    </div>
</template>

<script>

import Form from '../Form/form'
import axios from 'axios'

export default {
  components: {
    Form
  },
  methods: {
    submittedForm(formData) {
      axios.post('https://admin.wobiz.com.ar/api/auth/admin/signin', {
        username: formData.email.value,
        password: formData.password.value
      })
      .then(rta => console.log(rta))
      .catch(error => console.log(error))
    }
  }
}
</script>

<style scoped>
.box {
  position: relative;
  padding: 30px 50px;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: 6px;
}
.box .col {
  padding: 0;
}
.logo {
  width: 130px;
}
h2 {
  font-size: 26px;
  font-weight: 700;
  font-family: Roboto, sans-serif;
}
.greenish-blue-text {
  color: #163a49;
}
</style>