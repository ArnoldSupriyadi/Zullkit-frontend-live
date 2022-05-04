<script setup>
import { ref, onMounted } from "vue";
import Items from "../Items.vue";
import axios from "axios";

const items = ref([]);

async function GetItemsData() {
  try {
    const response = await axios.get("https://zullkit-backend.buildwithangga.id/api/products");
    items.value = response.data.data.data;
  } catch (error) {
    console.log(error);
  }
}

onMounted(() => {
  GetItemsData();
});
</script>
<template>
  <div class="container px-4 mx-auto my-16 md:px-12">
    <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">New Items</h2>
    <div class="flex flex-wrap -mx-1 lg:-mx-4">
      <Items v-for="item in items" :id="item.id" :key="item.id" :title="item.name" :description="item.subtitle" :image="item.thumbnails" />
    </div>
  </div>
</template>
