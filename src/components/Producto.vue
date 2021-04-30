<template>
  <div class="card my-5">
    <div class="card-body">
      <h5 class="text-center card-title">{{ producto.titulo }}</h5>
      <img :src="producto.imagen" alt="image" width="280" height="150" />
      <p class="text-center text-muted card-text display-4">
        $ {{ Number(producto.precio).toFixed() }}
      </p>
      <button
        @click="addShoppingCart(producto)"
        class="btn btn-primary form-control"
        :disabled="stateOnCart"
      >
        {{ stateOnCart ? "Agregado" : "Agregar al carrito" }}
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Producto",
  props: ["producto", "stateOnCart"],
  methods: {
    addShoppingCart(producto) {
      this.$emit("addCart", producto);
    }
  }
};
</script>
<style lang=""></style>
