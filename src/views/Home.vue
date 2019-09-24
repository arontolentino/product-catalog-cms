<template>
  <div class="home">
    <div v-for="(liquor, index) in liquors" :key="index">
      <h1>{{ liquor.product_name }}</h1>
      <h2>{{ liquor.product_description }}</h2>
    </div>
  </div>
</template>

<script>
import { butter } from "@/buttercms";

export default {
  name: "home",
  data() {
    return {
      liquors: []
    };
  },
  methods: {
    getProducts() {
      butter.content.retrieve(["liquor"]).then(res => {
        this.liquors = res.data.data.liquor;
        console.log(this.liquors);
      });
    }
  },
  created() {
    this.getProducts();
  }
};
</script>
