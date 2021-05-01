<template>
  <div>
    <div>{{ title }}</div>
    <div>
      <ul class="list-group">
        <li v-for="(item, index) in items" :key="index" class="list-group-item">
          {{ item.titulo }} - {{ item.precio }}
          <button
            @click="removeItem(item)"
            class="btn badge badge-danger float-right ml-1"
          >
            Eliminar
          </button>
        </li>
      </ul>
    </div>
    <div class="card p-3 my-5">
      <h4 class="text-center">Total: ${{ total }}</h4>
    </div>
    <button
      :disabled="items.length === 0"
      @click="$emit('pagar')"
      class="btn btn-info form-control"
    >
      Pagar Ahora
    </button>
  </div>
</template>
<script>
export default {
  name: "Carrito",
  props: ["items"],
  computed: {
    total() {
      return this.items.reduce(
        (acumulator, item) => acumulator + Number(item.precio),
        0
      );
    }
  },
  data() {
    return {
      title: "Tus Productos son:"
    };
  },
  methods: {
    removeItem(item) {
      this.$emit("remove-Item", item);
    }
  }
};
</script>
