<template>
    <div class="foot-navigator-container">
        <div class="foot-navigator">
            <div class="nav-item">
                <i class="bi bi-house"></i>
                <NuxtLink to="#">Home</NuxtLink>
            </div>
            <div class="nav-item">
                <i class="bi bi-coin"></i>
                <NuxtLink to="#">Earn</NuxtLink>
            </div>
            <div class="nav-item">
                <i class="bi bi-people"></i>
                <NuxtLink to="#">Frens</NuxtLink>
            </div>
        </div>
    </div>
</template>

<style scoped>
.foot-navigator-container {
    position: fixed;
    bottom: 0;
    width: 100%; height: auto;
    background-color: rgb(50, 0, 100);
    box-shadow: 0px -2px 2px rgba(0, 0, 0, 0.1);
} 

.foot-navigator {
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 0.45rem;
    width: 100%;
    height: 100%;
}

.nav-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 0.6rem;
    font-family: "Rubik", serif;
    font-optical-sizing: auto;
    font-weight: 500;
    font-style: normal;
}   

.nav-item :deep(a) {
    text-decoration: none;
    color: rgb(230, 200, 255);
}

.nav-item :deep(i) {
    font-size: 1.1rem;
    margin-bottom: 0.1rem;
    color: rgb(230, 200, 255);
}
</style>