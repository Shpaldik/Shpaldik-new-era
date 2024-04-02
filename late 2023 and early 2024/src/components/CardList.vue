<script setup>
import { inject } from "vue";
import Cards from "./Cards.vue";

defineProps({
  items: Array,
});

const emit = defineEmits(["AddToFavorite", "addToCart"]);
</script>

<template>
  <div class="grid grid-cols-4 gap-5" v-auto-animate>
    <Cards
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :onClickFavorite="() => emit('AddToFavorite', item)"
      :onClickAdd="() => emit('addToCart', item)"
      :isFavorite="item.isFavorite"
      :isAdded="item.isAdded"
    />
  </div>
</template>
