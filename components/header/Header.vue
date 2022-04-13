<template>
  <div>
    <div class="navber navber-expand-md fixed-top">
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand><h3>Vue Shop</h3></b-navbar-brand>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item><NuxtLink to="#home">Home</NuxtLink></b-nav-item>
            <b-nav-item><NuxtLink to="#product">Product</NuxtLink></b-nav-item>
            <b-nav-item><NuxtLink to="#about">About</NuxtLink></b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input
                size="sm"
                class="mr-sm-2"
                placeholder="Search"
              ></b-form-input>
            </b-nav-form>
            <b-button @click="showSignInModal" variant="light">
              SignIn
            </b-button>
            <b-button @click="showSignUpModal" variant="light">
              SignUp
            </b-button>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <modal name="Sign-In-Modal" :width="400" :height="370" :adaptive="true">
      <h1>LogIn Please</h1>
      <Login />
    </modal>
    <modal name="Sign-Up-Modal" :width="400" :height="400" :adaptive="true">
      <h1>Create New Account</h1>
      <Signup />
    </modal>
  </div>
</template>

<script>
export default {
  methods: {
    showSignInModal() {
      this.$modal.show('Sign-In-Modal')
      this.$modal.hide('Sign-Up-Modal')
    },
    showSignUpModal() {
      this.$modal.show('Sign-Up-Modal')
      this.$modal.hide('Sign-In-Modal')
    },
  },
}
</script>

<style scoped>
a {
  color: white;
  text-decoration: none;
}
button {
  margin-right: 5px;
}

.form {
  padding: 20px;
}
</style>
