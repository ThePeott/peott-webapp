<script setup>
defineProps({
    enable: {
        type: Boolean,
        default: true
    }
})
</script>

<template>
  <div class="coin-container">
    <div :class="enable ? 'coin-c' : 'coin-c disabled'">
        <div class="coin-c-inner">
          <span class="coin-inner-text">
            Z
          </span>
        </div>
    </div>
  </div>
</template>

<style scoped>
.coin-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.coin-c {
  width: 16rem;
  height: 16rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  box-shadow: 0 4px 12px rgba(255, 215, 0, 0.2);
}

.coin-c.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  filter: grayscale(0.8);
}

.coin-c:hover:not(.disabled) {
  transform: scale(1.02);
  box-shadow: 0 6px 16px rgba(255, 215, 0, 0.3);
}

.coin-c:active:not(.disabled) {
  transform: scale(0.98);
}

.coin-c-inner {
  width: 12rem;
  height: 12rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #ffd700 0%, #ffb700 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: inset 0px 0px 8px rgba(0, 0, 0, 0.3);
  transform: rotate(30deg);
}

.coin-inner-text {
  user-select: none;
  font-size: 7rem;
  color: rgb(255, 246, 201);
  font-family: "Sigmar", serif;
  opacity: 0.5;
}
</style>