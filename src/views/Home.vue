<template>
  <div class="home">
    <section class="hero is-dark is-medium">
      <!-- Hero head: will stick at the top -->
      <div class="hero-head">
        <nav class="navbar">
          <div class="container">
            <div id="navbarMenuHeroA" class="navbar-menu">
              <div class="navbar-end">
                <a class="navbar-item is-active">Home</a>
                <a class="navbar-item">Brands</a>
                <a class="navbar-item">About</a>
                <a class="navbar-item">Contact</a>
              </div>
            </div>
          </div>
        </nav>
      </div>

      <!-- Hero content: will be in the middle -->
      <div class="hero-body">
        <div class="container has-text-centered">
          <h1 class="title is-1">Perennial Brands</h1>
          <h2
            class="subtitle is-4"
          >Sure, we’re passionate about great beer, but it’s our longstanding relationship with our drinkers that really inspires us. We want to be their first choice for any occasion, so we offer a broad range of brands to suit any taste—we have beer for every beer lover.</h2>
        </div>
      </div>
    </section>

    <section class="product">
      <div class="container">
        <div class="card" v-for="(liquor, index) in liquors" :key="index">
          <div class="card-image">
            <figure class="image">
              <img v-bind:src="liquor.product_image" alt="Placeholder image" />
            </figure>
          </div>
          <div class="card-content">
            <div class="content">
              <h1 class="title is-4">{{ liquor.product_name }}</h1>
              <p>{{ liquor.product_description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
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

<style>
.hero {
  background-image: url("https://images.unsplash.com/photo-1563970116818-6dd8b5fb725f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1650&q=80");
  background-size: cover;
  background-position: bottom right;
}

.container {
  max-width: 1000px;
}

.product {
  padding-top: 55px;
}

.product .container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.card {
  width: 315px;
  border-radius: 5px;
  margin-bottom: 27.5px;
  border: none;
  text-align: center;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  transition: all 0.3s ease;
}

.card:hover {
  -webkit-transform: scale(1.05);
  -ms-transform: scale(1.05);
  transform: scale(1.05);
}

.image img {
  width: 50%;
  margin: 0 auto;
}
</style>