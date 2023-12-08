<!-- <script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark   ">
  <div class="container  ">
    <RouterLink class="navbar-brand" to="/">Navbar</RouterLink>
    
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <RouterLink class="nav-link active" to="/">Home</RouterLink>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link " to="/about">About Us</RouterLink>
        </li>
        <li class="nav-item">
          <RouterLink class="nav-link " to="/Students">Students</RouterLink>
        </li>
      
     
      </ul>
      
    </div>
  </div>
</nav>
    

      
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
 -->
<template>
  <main id="app" @mousemove="mousemove">
    <section class="products">
      <Product v-for="product in products" :key="product.color" :product="product" />
    </section>
  </main>
</template>

<script>
import Product from './components/product.vue';
import blueShoeImage from './assets/blue-shoe.png';
import greenShoeImage from './assets/green-shoe.png';
import pinkShoeImage from './assets/pink-shoe.png';


export default {
  name: 'app',
  components: {
    Product
  },
  data() {
    return {
      products: [
        {
          title: 'Nike Air Max',
          color: 'green',
          bgtext: 'NIKE',
          src: blueShoeImage
        },
        {
          title: 'Nike flex',
          color: 'blue',
          bgtext: 'AIR',
          src: greenShoeImage
        },
        {
          title: 'Nike Roche Runs',
          color: 'oink',
          bgtext: 'MAX',
          src: pinkShoeImage
        },

      ]
    }
  },
  methods: {
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll('.products .product');

      for (let i = 0; i < products.length; i++) {
        let product = products[i];

        let product_image = product.querySelector('.product-image-wrap');

        let img_x = mouseX - this.coords(product_image).x;
        let img_y = mouseY - this.coords(product_image).y;
        product_image.style.transform = `translateY(-${img_y / 40}px) translateX(-${img_x / 40}px) translateZ(100px)`;

        let bgtext = product.querySelector('.bg-text');
        let bg_x = mouseX - this.coords(bgtext).x;
        bgtext.style.transform = `translateX(${bg_x / 25}px)`;
      }
    },
    coords(el) {
      let coords = el.getBoundingClientRect();

      return {
        x: coords.left / 2,
        y: coords.top / 2
      }
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'montseratt', sans-serif;
}

main {
  width: 100vw;
  min-height: 100vh;
  overflow: hidden;

  background-color: #EEE;
  display: flex;
  justify-content: center;
  align-items: center;
}

.products {
  display: flex;
  max-width: 1280px;
  padding: 25px;
  margin: 0 auto;
}
</style>