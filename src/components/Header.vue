<template>
  <header>
    <div class="hamburger" @click="isOpen = !isOpen">
      ☰
    </div>
    <nav v-if="isOpen">
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'
const isOpen = ref(false)
</script>