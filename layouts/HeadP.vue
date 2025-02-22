<template>
    <div class="head-layout-container">
        <div class="special-subscription">
            <i class="bi bi-question-circle-fill"></i>
        </div>
        <div class="app-logo">
            ThePeott
        </div>
        <div class="settings">
            <i class="bi bi-gear-fill"></i>
        </div>
    </div>
</template>

<style scoped>
.head-layout-container{
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    height: 60px;
    box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.1);
}

.special-subscription {
    background-color: #ededed;
    border-radius: 50%;
    padding: 4px;
}

.app-logo {
    font-family: "Sigmar", serif;
    font-weight: 400;
    font-style: italic;
    font-size: 1.4rem;
}

.settings {
    background-color: #ededed;
    border-radius: 50%;
    padding: 4px;
}

.special-subscription i, .settings i {
    font-size: 1.1rem;
}

</style>