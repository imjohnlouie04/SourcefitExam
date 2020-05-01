<template>
  <div class="contact-form">
    <div class="header-title">Contact Us</div>
    <form action="">
      <div class="form-control">
        <label for="name">Who are you?</label>
        <input type="text" id="name" v-model="user.name">
      </div>

      <div class="form-control">
        <label for="email">Where can we spam you?</label>
        <input type="email" id="email" v-model="user.email">
      </div>

      <div class="form-control">
        <label for="phone">Where can we call you at night?</label>
        <input type="text" id="phone" v-model="user.phone">
      </div>

      <div class="form-control">
        <label for="message">What do you want to tell us?</label>
        <input type="text" id="message" v-model="user.message">
      </div>

      <div class="group-btn">
        <button class="btn action outline" type="reset">
          Reset the form
        </button>
        <button class="btn action" type="reset">
          Send your message now
        </button>
      </div>
    </form>
  </div>
</template>
<script>

export default {
  data() {
    return {
      user: {}
    }
  },
}
</script>

<style scoped>
.contact-form {
  min-height: 600px;
  background-image: url('../assets/images/contact-us-bg.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  padding: 15px;
}
</style>