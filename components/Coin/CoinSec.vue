<script setup lang="ts">
import { ref, onMounted } from 'vue';
import gsap from 'gsap';

const props = defineProps({
  enable: {
    type: Boolean,
    default: false
  }
});

const tapPower = ref(1);
const tapPowerMultiplier = ref(50);

const energyLeft = ref(10000);
const totalEnergy = ref(10000);

const coins = ref(0);

const animationElements = ref<HTMLElement[]>([]);

function createPlusOneAnimation(event: MouseEvent) {
  if (!props.enable || energyLeft.value <= 0) return;
  
  event.preventDefault();
  
  energyLeft.value = Math.max(0, energyLeft.value - (tapPower.value * tapPowerMultiplier.value));

  const containerEl = document.querySelector('.coin') as HTMLElement;
  
  const rect = containerEl.getBoundingClientRect();
  const x = event.clientX - rect.left;
  const y = event.clientY - rect.top;
  
  const tapCounterEl = document.createElement('div');
  tapCounterEl.classList.add('plus-tap-animation');

  tapCounterEl.innerHTML = `<span>+${tapPower.value * tapPowerMultiplier.value}</span>`;
  
  tapCounterEl.style.position = 'absolute';
  tapCounterEl.style.left = `${x}px`;
  tapCounterEl.style.top = `${y}px`;
  tapCounterEl.style.pointerEvents = 'none';
  tapCounterEl.style.zIndex = '100';
  
  containerEl.appendChild(tapCounterEl);
  animationElements.value.push(tapCounterEl);

  coins.value += (tapPower.value * tapPowerMultiplier.value)

  gsap.to(tapCounterEl, {
    y: -80,
    scale: 1.2,
    opacity: 0,
    duration: 1,
    ease: "power2.out",
    onComplete: () => {
      if (containerEl.contains(tapCounterEl)) {
        containerEl.removeChild(tapCounterEl);
      }
      animationElements.value = animationElements.value.filter(el => el !== tapCounterEl);
    },
  });
}

onMounted(() => {
  return () => {
    animationElements.value.forEach(el => {
      if (el.parentNode) {
        el.parentNode.removeChild(el);
      }
    });
  };
});
</script>

<template>
  <div class="coin-energy-balance-container">
    <div class="balance-indicator">
      <div class="balance-container">
        <i class="bi bi-coin"></i>
        <h1>{{ coins }}</h1>
      </div>
    </div>
    <div class="container-coin-energy">
      <div class="energy-container">
        <div class="energy-indicator">
          <div class="energy-bar" :style="{ height: `${(energyLeft / totalEnergy) * 100}%` }"></div>
          <span>{{ energyLeft }} / {{ totalEnergy }}</span>
        </div>
      </div>
      <div class="coin-container">
        <div 
          class="coin-wrapper"
          @click="createPlusOneAnimation"
          :class="{ 'disabled': !enable || energyLeft <= 0 }"
        >
          <div class="coin">
            <div class="coin-inner">
              <span class="coin-text">Z</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.container-coin-energy {
  width: 100%;
  display: flex;
  justify-content: center;
  gap: 1rem; 
  align-items: center;
  position: relative;
}

.balance-container {
  width: 50%;
  max-width: 300px;
  backdrop-filter: blur(10px); 
  padding: 10px 20px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

.balance-indicator {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  color: rgb(230, 200, 255);
}

.balance-container i {
  font-size: 1.4rem;
}

.balance-container h1 {
  font-family: "Courier Prime", serif;
  font-size: 2rem;
  font-weight: 800;
  font-style: normal;
}

.coin-container {
  width: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.coin-wrapper {
  position: relative;
  cursor: default;
}

.coin {
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

.coin-wrapper.disabled .coin {
  opacity: 0.5;
  filter: grayscale(0.8);
}

.coin-wrapper:hover:not(.disabled) .coin {
  transform: scale(1.02);
  box-shadow: 0 10px 20px rgba(255, 215, 0, 0.3),
              10px 0 20px rgba(255, 215, 0, 0.3),
              0 -10px 20px rgba(255, 215, 0, 0.3),
              -10px 0 20px rgba(255, 215, 0, 0.3);
}

.coin-wrapper:active:not(.disabled) .coin {
  transform: scale(0.98);  
}

.coin-inner {
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

.coin-text {
  user-select: none;
  font-size: 7rem;
  color: rgb(255, 246, 201);
  font-family: "Sigmar", serif;
  opacity: 0.5;
}

.plus-tap-animation {
  position: absolute;
  z-index: 1000;
  pointer-events: none;
  user-select: none;
}

.plus-tap-animation span {
  display: block;
  font-family: "SF Pro Display", "Rubik", sans-serif;
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
  user-select: none;
}

.energy-container {
  width: 5%;
}

.energy-indicator {
  background-color: rgb(50, 0, 100);
  width: 100%;
  border-radius: 15px;
  height: 12rem;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.energy-indicator .energy-bar {
  background-color: rgb(230, 200, 255);;
  width: 100%;
  position: absolute;
  bottom: 0;
  transition: height 0.2s ease;
}

.energy-indicator span {
  position: absolute;
  writing-mode: vertical-rl;
  width: 100%;
  text-align: center;
  white-space: nowrap;
  transform: rotate(180deg);
  color: rgb(127,0,212);
  font-family: "SF Pro Display", "Rubik", sans-serif;
  font-size: 0.8rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>
