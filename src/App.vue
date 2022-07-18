<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <headers class="p-14">
    <div >
      <!-- <HelloWorld msg="You did it!" /> -->

      <nav>
        <!-- <RouterLink class="flex justify-center text-4xl text-yellow" to="/">Home</RouterLink> -->
        <!-- <RouterLink to="/about">About</RouterLink> -->
      </nav>
    </div>
  </headers>

  <RouterView />
</template>

