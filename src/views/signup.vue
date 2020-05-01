<template>
  <div class="signup-form">
    <div class="header-title">Sign Up</div>
    <form action="">
      <div class="form-control">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="user.email">
      </div>

      <div class="form-control">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="user.password">
      </div>

      <p style="text-align: center">{{ response }}</p>

      <div class="group-btn">
        <button class="btn action" @click="register">
          Register
        </button>
      </div>
    </form>
  </div>
</template>
<script>
const url = "https://reqres.in/api/register"
import axios from 'axios'
export default {
  data() {
    return {
      user: {},
      response: ''
    }
  },
  methods: {
    register () {
      axios.post(url, this.user).then((response) => {
        console.log(response.data)
        this.response = 'Registration Successful';
      }).catch(error => {
        this.response = error.response.data;
      });
    }
  },
}
</script>

<style scoped>

@media (min-width: 1024px) {
  .form-control label {
    width: 30%;
  }
}
</style>