<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps({
  width: {
    type: Number,
    default: 256 // Default 16rem (16 * 16 = 256px)
  },
  height: {
    type: Number,
    default: 256
  }
});

// Compute inner coin size (75% of outer coin)
const innerSize = computed(() => Math.min(props.width, props.height) * 0.75);

// Compute font size (35% of outer coin size)
const fontSize = computed(() => Math.min(props.width, props.height) * 0.35);
</script>

<template>
  <div class="ic-coin-wrapper">
    <div class="ic-coin" :style="{ width: `${width}px`, height: `${height}px` }">
      <div 
        class="ic-coin-inner"
        :style="{ width: `${innerSize}px`, height: `${innerSize}px` }"
      >
        <span class="ic-coin-text" :style="{ fontSize: `${fontSize}px` }">Z</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.ic-coin-wrapper {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.ic-coin {
  border-radius: 50%;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(255, 215, 0, 0.2);
}

.ic-coin-inner {
  border-radius: 50%;
  background: linear-gradient(135deg, #ffd700 0%, #ffb700 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: inset 0px 0px 8px rgba(0, 0, 0, 0.3);
  transform: rotate(30deg);
}

.ic-coin-text {
  user-select: none;
  color: rgb(255, 246, 201);
  font-family: "Sigmar", serif;
  opacity: 0.5;
}
</style>
