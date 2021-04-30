<template>
  <div id="app">
    <div class="row">
      <div class="col-md-12 bg-red">TITLE OF MY STORE</div>
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="prod in productos" :key="prod.id">
            <producto
              :producto="prod"
              v-on:addCart="addProductCart"
              :stateOnCart="stateOnCart(prod)"
            ></producto>
          </div>
        </div>
      </div>
      <div class="col-md-4 my-4">
        <carrito :items="carrito" v-on:remove-Item="removeProduct"></carrito>
      </div>
    </div>
  </div>
</template>

<script>
import Producto from "./components/Producto.vue";
import Carrito from "./components/Carrito.vue";
import productos from "./productos.json";

export default {
  name: "App",
  components: {
    Producto,
    Carrito
  },
  data() {
    return {
      productos,
      carrito: []
    };
  },
  methods: {
    addProductCart(producto) {
      this.carrito.push(producto);
    },
    stateOnCart(producto) {
      const item = this.carrito.find(item => item.id === producto.id);
      if (item) {
        return true;
      } else {
        return false;
      }
    },
    removeProduct(producto) {
      this.carrito = this.carrito.filter(item => item.id != producto.id);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
