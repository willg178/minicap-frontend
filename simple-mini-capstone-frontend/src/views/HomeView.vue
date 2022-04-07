<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to The Store!",
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("http://localhost:3000/products.json").then((response) => {
        this.products = response.data;
        console.log("All products", this.products);
      });
    },
    createProduct: function () {
      console.log("Making a new product!");

      var params = {
        name: "example name",
        description: "example description",
        price: "example price",
        image_url: "example image_url",
      };
      axios
        .post("http://localhost:3000/products.json", params)
        .then((response) => {
          console.log("Success", response.data);
          this.recipes.push(response.data);
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>New Product!</h2>
    <div>
      <div>
        name:
        <input type="text" v-model="newProductParams.name" />
        description:
        <input type="text" v-model="newProductParams.description" />
        price:
        <input type="text" v-model="newProductParams.price" />
        image_url:
        <input type="text" v-model="newProductParams.image_url" />
      </div>
    </div>

    <button v-on:click="createProduct()">Create</button>
    <div v-for="product in products" v-bind:key="product.id">
      <h2>Name: {{ product.name }}</h2>
      <img :src="product.image_url" />
      <p>Description: {{ product.description }}</p>
    </div>
  </div>
</template>

<style></style>
