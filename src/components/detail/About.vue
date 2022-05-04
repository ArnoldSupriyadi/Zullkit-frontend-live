<script setup>
import { ref, onMounted } from "vue";
import { RouterLink, useRoute } from "vue-router";
import axios from "axios";

const route = useRoute();
const item = ref({});

async function getProduct() {
  try {
    const response = await axios.get("https://zullkit-backend.buildwithangga.id/api/products?id=" + route.params.id);
    item.value = response.data.data;
    console.log(response);
  } catch (error) {
    console.log(error);
  }
}

onMounted(() => {
  getProduct();
});
</script>
<template>
  <section class="" id="orders">
    <h1 class="mt-8 mb-3 text-lg font-semibold">About</h1>
    <div class="text-gray-500" v-html="item.description"></div>
  </section>
</template>
