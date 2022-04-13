<template>
  <div class="container-fluid">
    <h2>Product Page</h2>

    <hr />
    <div>
      <h1>Basick</h1>
      <b-form>
        <div class="form-group">
          <b-form-input
            type="text"
            id="name"
            v-model="name"
            placeholder="Product Name"
          ></b-form-input>
        </div>
        <div class="form-group">
          <b-form-input
            type="text"
            id="price"
            v-model="price"
            placeholder="Price"
          ></b-form-input>
        </div>
        <div class="form-group">
          <b-button @click="saveData" class="btn-primary">Save Data</b-button>
        </div>
      </b-form>
    </div>
    <div>
      <h2>Product List</h2>
      <table class="table table-striped">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Price</th>
            <th scope="col">Modify</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(product, index) in products" :key="index">
            <td>{{ product.data().name }}</td>
            <td>{{ product.data().price }}</td>
            <td>
              <button class="btn btn-primary" @click="showModal">Edit</button>
              <button class="btn btn-danger" @click="deleteData(product.id)">
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <modal
      name="edit-products-modal"
      :width="400"
      :height="370"
      :adaptive="true"
    >
      <h2>Edit Product</h2>
      <form class="form p-3">
        <div class="form-group">
          <input
            class="form-control"
            type="text"
            id="name"
            placeholder="Product Name"
          />
        </div>
        <div class="form-group">
          <input
            class="form-control"
            type="text"
            id="price"
            placeholder="Price"
          />
        </div>
        <button @click="hideModal" class="btn btn-primary">Close Modal</button>
        <button @click="saveData" class="btn btn-primary">Save Data</button>
      </form>
    </modal>
  </div>
</template>

<script>
export default {
  layout: 'sidebar',

  data() {
    return {
      name: '',
      price: '',
      products: [],
    }
  },
  methods: {
    saveData() {
      this.$fire.firestore
        .collection('Products')
        .add({
          name: this.name,
          price: this.price,
        })
        .then(() => {
          this.reset()
        })
        .catch((error) => {
          console.log(error)
        })
    },
    reset() {
      this.name = ''
      this.price = ''
    },

    getData() {
      this.$fire.firestore
        .collection('Products')
        .get()
        .then((querySnapshot) => {
          this.products = []
          querySnapshot.forEach((doc) => {
            this.products.push(doc)
          })
        })
        .catch((error) => {
          console.log(error)
        })
    },
    deleteData(id) {
      this.$fire.firestore
        .collection('Products')
        .doc(id)
        .delete()
        .then(() => {
          alert('Data Deleted')
          this.getData()
        })
        .catch((error) => {
          console.log(error)
        })
    },
    showModal() {
      this.$modal.show('edit-products-modal')
    },
    hideModal() {
      this.$modal.hide('edit-products-modal')
    },
  },
  created() {
    this.getData()
  },
}
</script>

<style></style>
