<template>
  <div id="product">
    <div class="container px-5 py-6" id="featured-3">
      <h2 class="pb-2 border-bottom">Our Products</h2>
      <div class="row g-3 py-3 row-cols-1 row-cols-lg-3">
        <div class="feature col card">
          <div class="feature-icon bg-gradient">
            <img src="../../static/image/product/decstop.png" alt="" />
          </div>
          <h2>Surface PC</h2>
          <p>
            Paragraph of text beneath the heading to explain the heading. We'll
            add onto it with another sentence and probably just keep going until
            we run out of words.
          </p>
          <NuxtLink to="#" class="btn btn-primary"> Add To Cart </NuxtLink>
        </div>
        <div class="feature col card">
          <div class="feature-icon bg-gradient">
            <img src="../../static/image/product/laptop.png" alt="" />
          </div>
          <h2>Surface Laptop</h2>
          <p>
            Paragraph of text beneath the heading to explain the heading. We'll
            add onto it with another sentence and probably just keep going until
            we run out of words.
          </p>
          <NuxtLink to="#" class="btn btn-primary"> Add To Cart </NuxtLink>
        </div>
        <div class="feature col card">
          <div class="feature-icon bg-gradient">
            <img src="../../static/image/product/studio.png" alt="" />
          </div>
          <h2>Surface Studioe</h2>
          <p>
            Paragraph of text beneath the heading to explain the heading. We'll
            add onto it with another sentence and probably just keep going until
            we run out of words.
          </p>
          <NuxtLink to="#" class="btn btn-primary"> Add To Cart </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
img {
  height: 200px;
  width: 200px;
  object-fit: cover;
}

.card {
  padding: 10px;
  grid-gap: 5px;
}
</style>