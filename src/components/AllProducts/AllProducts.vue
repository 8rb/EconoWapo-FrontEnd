<template>
    <div class="products mt-4">
        <div class="product-box mt-3">
            <div class="col-12 mt-4">
                <div class="col-12 product-box">
                    <div class="row orders-title">
                        <div class="col-10 mt-4">
                            <h3 class="title mr-3">All my Products</h3>
                        </div>
                        <div class="col-2 mt-4">
                            <b-button class="btn text-success" type="submit" variant="primary" v-on:click="registerProduct()">Registrar Producto</b-button>
                        </div>
                    </div>
                    <div class="row orders-title mt-5">
                        <div class="col-1">
                            <h3 class="subtitle">ID</h3>
                        </div>
                        <div class="col-3">
                            <h3 class="subtitle">Name</h3>
                        </div>
                        <div class="col-4">
                            <h3 class="subtitle">Description</h3>
                        </div>
                        <div class="col-1">
                            <h3 class="subtitle">Price</h3>
                        </div>
                        <div class="col-1">
                            <h3 class="subtitle">Image</h3>
                        </div>
                        <div class="col-1">
                            <h3 class="subtitle">Modify</h3>
                        </div>                
                        <div class="col-1">
                            <h3 class="subtitle">Remove</h3>
                        </div>
                    </div>
                    <div class="row orders-title">
                        <div class="col-12">
                            <li v-for="(product, index) in products" :key="index" class="">
                                <div class="row orders-item-box align-items-center">
                                    <div class="col-1">
                                        <h3 class="subtitle">{{product.id}}</h3>
                                    </div>
                                    <div class="col-3">
                                        <h3 class="subtitle">{{product.name}}</h3>
                                    </div>
                                    <div class="col-4">
                                        <h3 class="subtitle">{{product.description}}</h3>
                                    </div>
                                    <div class="col-1">
                                        <h3 class="subtitle">S/.{{product.price.toFixed(2)}}</h3>
                                    </div>
                                    <div class="col-1">
                                        <a href="https://imgbb.com/"><img  class="order-img" :src="product.image" :alt="product.name" border="0" /></a>
                                    </div>
                                    <div class="col-1">
                                        <router-link to="/editProduct">
                                            <a class="fas fa-pencil-alt fa-2x edit-icon"></a>
                                        </router-link>
                                    </div>                
                                    <div class="col-1">
                                        <button class="btn-icon" v-on:click="removeProduct"><i class="fas fa-trash fa-2x edit-icon"></i></button>
                                    </div>
                                </div>
                            </li>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'Orders',
    created() {
      this.products = this.$store.getters.products;
    },
      mounted () {
      this.cart = this.$store.getters.cart;
      this.products = this.$store.getters.products;
    },
    data() {
      return {
        checked: null,
        aux: null,
        quantity: null,
        products: [],
      }
    },
    methods: {
        registerProduct() {
            this.$router.push('/createProduct');
        },
        editProduct() {
            this.$router.push('/editProduct');
        },
        removeProduct() {
            alert("Removing product...")
        }
    }
  }
</script>