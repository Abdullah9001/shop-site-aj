<template>
  <div class="page-wrapper chiller-theme toggled">
    <a id="show-sidebar" class="btn btn-sm btn-dark" href="#" @click="addMenu">
      <i class="fas fa-bars"></i>
    </a>
    <nav id="sidebar" class="sidebar-wrapper">
      <div class="sidebar-content">
        <div class="sidebar-brand">
          <a href="#">Vue Shop</a>
          <div id="close-sidebar" @click="closeMenu">
            <i class="fas fa-times"></i>
          </div>
        </div>
        <div class="sidebar-header">
          <div class="user-pic">
            <img src="../static/user.png" alt="" />
          </div>
          <div class="user-info">
            <span class="user-name"
              >Jhon
              <strong>Smith</strong>
            </span>
            <span class="user-role">Administrator</span>
            <span class="user-status">
              <i class="fa fa-circle"></i>
              <span>Online</span>
            </span>
          </div>
        </div>
        <!-- sidebar-header  -->
        <div class="sidebar-search">
          <div>
            <div class="input-group">
              <input
                type="text"
                class="form-control search-menu"
                placeholder="Search..."
              />
              <div class="input-group-append">
                <span class="input-group-text">
                  <i class="fa fa-search" aria-hidden="true"></i>
                </span>
              </div>
            </div>
          </div>
        </div>
        <!-- sidebar-search  -->
        <div class="sidebar-menu">
          <ul>
            <li class="header-menu">
              <span>Menu</span>
            </li>

            <li>
              <NuxtLink to="/admin/overview">
                <i class="fa-solid fa-chart-line"></i>
                <span>Overview</span>
              </NuxtLink>
            </li>
            <li>
              <a href="#">
                <i class="fa-brands fa-amazon"></i>
                <span>Products</span>
              </a>
            </li>
            <li>
              <a href="#">
                <i class="fa-solid fa-cart-shopping"></i>
                <span>Order</span>
              </a>
            </li>
            <li>
              <a href="#">
                <i class="fa-solid fa-power-off"></i>
                <span>Logout</span>
              </a>
            </li>
          </ul>
        </div>
        <!-- sidebar-menu  -->
      </div>
    </nav>
    <!-- sidebar-wrapper  -->
    <main></main>
    <!-- page-content" -->
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped></style>
