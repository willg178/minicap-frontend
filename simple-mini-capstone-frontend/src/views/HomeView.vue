<script>
export default {
  data: function() {
    return {
      message: "Welcome to The Cookbook!"
      recipes: [
        {id: 1, title: "Eggs", chef: "Chicken"}
        {id: 2, title: "Watermelon", chef: "Watermelon Plant"}
      ],
    };
  },
  created: function() {},
  methods: {}
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2 v-for="recipe in recipes">{{ recipe }}</h2>
  </div>
</template>

<style></style>
