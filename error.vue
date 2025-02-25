<script setup lang="ts">
import type { NuxtError } from '#app'

defineProps({
  error: Object as () => NuxtError
})

const handleError = () => clearError({ redirect: '/' })
</script>

<template>
  <div class="error-container">
    <div class="error-details">
      <h1>{{ error?.statusCode }}</h1>
      <p>{{ error?.statusCode === 404 ? `Page not found` : 'An error occured'  }}</p>
    </div>

    <button @click="handleError">Go back home</button>
  </div>
</template>

<style> 
.error-container {
  width: 100svw;
  height: 100svh;
  background-color: black;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.error-details {
  text-align: center;
}

.error-details h1{
  font-family: "Playwrite IT Moderna", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}

.error-details p{
  font-family: "Playwrite IT Moderna", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
}

.error-container button{
  padding: 15px 20px;
  background-color: white;
  color: black;
  border: none;
  cursor: pointer;
  margin-top: 20px;
  font-family: "Playwrite IT Moderna", serif;
  font-optical-sizing: auto;
  font-weight: 400;
  font-style: normal;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.9rem;
  transition: all 0.3s;
  border-radius: 20px;
}
</style> 
