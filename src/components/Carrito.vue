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
  </div>
</template>
<script>
export default {
  name: "Carrito",
  props: ["items"],
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
