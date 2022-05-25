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
            v-model="product.name"
            placeholder="Product Name"
          ></b-form-input>
        </div>
        <div class="form-group">
          <b-form-input
            type="text"
            id="price"
            v-model="product.price"
            placeholder="Price"
          ></b-form-input>
        </div>
        <div class="form-group">
          <b-button @click="saveData" variant="primary">Save Data</b-button>
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
              <b-button variant="primary" @click="editProduct(product)"
                >Edit</b-button
              >
              <b-button variant="danger" @click="deleteData(product.id)">
                Delete
              </b-button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <modal
      name="edit-products-modal"
      :width="400"
      :height="240"
      :adaptive="true"
    >
      <h2>Edit Product</h2>
      <form class="form p-3">
        <div class="form-group">
          <input
            class="form-control"
            type="text"
            v-modal="product.name"
            id="name"
            placeholder="Product Name"
          />
        </div>
        <div class="form-group">
          <input
            class="form-control"
            type="text"
            v-modal="product.price"
            id="price"
            placeholder="Price"
          />
        </div>
        <b-button @click="updateProduct()" variant="primary">Save Data</b-button>
      </form>
    </modal>
  </div>
</template>

<script>
export default {
  layout: 'sidebar',

  data() {
    return {
      product: {
        name: '',
        price: '',
      },
      products: [],
      activItem: '',
    }
  },
  methods: {
    saveData () {
      this.$fire.firestore
        .collection('Products')
        .add(this.product)
        .then(() => {
          this.product = {
            name: '',
            price: '',
          }
        })
        .catch(err => {
          console.log(err)
        })
    },

    getData () {
      this.$fire.firestore
        .collection('Products')
        .get()
        .then(snapshot => {
          snapshot.forEach(doc => {
            this.products.push(doc)
          })
        })
        .catch(err => {
          console.log(err)
        })
    },
    deleteData (id) {
      this.$fire.firestore
        .collection('Products')
        .doc(id)
        .delete()
        .then(() => {
          alert('Data Deleted')
          this.products = []
          this.getData()
        })
        .catch(err => {
          console.log(err)
        })
    },
    editProduct (product) {
      this.activItem = product.id
      this.product = product.data()
      this.$modal.show('edit-products-modal')
    },
  },
  updateProduct() {
    this.$fire.firestore
      .collection('Products')
      .doc(this.activItem.id)
      .update(this.product)
      .then(() => {
        this.$modal.hide('edit-products-modal')
        this.watcher()
      }) 
      .catch((error) => {
        console.log(error)
      })
  },
  watcher(){
    this.$fire.firestore
      .collection('Products')
      .onSnapshot((querySnapshot) => {
        this.products = []
        querySnapshot.forEach((doc) => {
          this.products.push(doc)
        })
      })
  },

  created() {
    this.getData()
  },
}
</script>

<style></style>
