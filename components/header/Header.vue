<template>
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
            <b-button size="sm" class="my-2 my-sm-0" type="submit"
              >Search</b-button
            >
          </b-nav-form>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>

  a{
    color: white;
    text-decoration: none;
  }
</style>