<template>
  <div class="form">
    <b-form-group id="input-group-1" label="Name:" label-for="input-2">
      <b-form-input
        id="input-1"
        v-model="name"
        placeholder="Enter Full Name"
        required
      ></b-form-input>
    </b-form-group>

    <b-form-group
      id="input-group-2"
      label="Email address:"
      label-for="input-2"
      description="We'll never share your email with anyone else."
    >
      <b-form-input
        id="input-2"
        v-model="email"
        type="email"
        placeholder="Enter email"
        required
      ></b-form-input>
    </b-form-group>

    <b-form-group id="input-group-3" label="Password:" label-for="input-3">
      <b-form-input
        id="input-3"
        v-model="password"
        placeholder="Enter password"
        required
      ></b-form-input>
    </b-form-group>

    <b-button type="submit" @click="register" variant="primary"
      >SignUp</b-button
    >
  </div>
</template>

<script>

export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
    }
  },
  methods: {
    register() {
      this.$fire.auth
        .createUserWithEmailAndPassword(this.email, this.password)
        .then((user) => {
          this.$router.replace({ path : '/admin' })
        })
        .catch((error) => {
          console.log(error)
        })
    },
  },
}
</script>

<style></style>
