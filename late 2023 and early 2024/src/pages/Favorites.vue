<script setup>
import { onMounted } from "vue";
import axios from "axios";

import CardList from "../components/CardList.vue";

const favorites = ref([]);

onMounted(async () => {
  try {
    const { data } = await axios.get(
      `https://490035188efe55d6.mokky.dev/favorites?_relations=items`
    );
  } catch (err) {
    console.log(err);
  }

  favorites.value = data.map(obj => obj.item);
});
</script>

<template>
  <h1>Мой закладки</h1>

  <CardList :items="favorites" />
</template>
