<template>
  <div class="form">
    <b-form-group
      id="input-group-1"
      label="Email address:"
      label-for="input-1"
      description="We'll never share your email with anyone else."
    >
      <b-form-input
        id="input-1"
        v-model="email"
        type="email"
        placeholder="Enter email"
        required
      ></b-form-input>
    </b-form-group>

    <b-form-group id="input-group-2" label="Password:" label-for="input-2">
      <b-form-input
        id="input-2"
        v-model="password"
        placeholder="Enter password"
        required
      ></b-form-input>
    </b-form-group>

    <b-button @click="logIn" type="submit" variant="primary">LogIn</b-button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    logIn() {
      this.$fire.auth
        .signInWithEmailAndPassword(this.email, this.password)
        .then((user) => {
          this.$router.replace({ path: '/admin' })
        })
        .catch((error) => {
          console.log(error)
        })
    },
  },
}
</script>

<style></style>
