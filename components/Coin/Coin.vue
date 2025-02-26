<template>
    <div class="coin-wrapper">
      <div class="coin">
        <div class="coin-inner">
          <span class="coin-text">Z</span>
        </div>
      </div>
    </div>
  </template>
  
  <style scoped>
  .coin-wrapper {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .coin {
    width: 16rem;
    height: 16rem;
    border-radius: 50%;
    background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 12px rgba(255, 215, 0, 0.2);
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
  </style>
  