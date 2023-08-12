<script setup lang="ts">
import { ref } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

export interface RouteMap {
  name: string;
  target?: string;
  to: string | NameStructure;
}

export interface NameStructure {
  name: string;
}

const urls = ref<RouteMap[]>([
  {
    name: 'Home',
    to: { name: 'home' },
  },
  {
    name: 'Test',
    to: { name: 'test' },
  },
  {
    name: 'About',
    target: '_blank',
    to: { name: 'about' },
  },
  {
    name: 'Contact',
    target: '_blank',
    to: '/contact',
  },
]);
</script>

<template>
  <header>
    <nav class="nav">
      <RouterLink class="router-link" v-for="(url, index) in urls" :key="index">
        {{ url.name }}
      </RouterLink>
    </nav>
  </header>
  <RouterView />
</template>

<style scoped>
.nav {
  display: flex;
  gap: 16px;
}

.router-link {
  text-decoration: none;
  color: darkred;
  font-size: 20px;
  font-weight: bold;
}

.router-link-active {
  color: darkgreen;
}
</style>
