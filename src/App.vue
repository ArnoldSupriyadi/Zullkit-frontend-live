<script setup>
import { RouterLink, RouterView } from "vue-router";
import Navbar from './components/layouts/navbar/Navbar.vue'
</script>

<template>
  <Navbar />
  <router-view />
</template>

<style>
  @import "@/assets/css/styles.css";
</style>
