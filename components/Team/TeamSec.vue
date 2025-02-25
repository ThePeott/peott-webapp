<template>
    <div class="team-sec">
        <h1>TeamName</h1>
        <p>{{ memberCount }} members</p>
    </div>
</template>

<script setup>
import { ref } from 'vue'
const memberCount = ref(200)
</script>

<style scoped>
.team-sec {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
    background: linear-gradient(to top, rgba(1, 1, 1, 0.9), transparent), 
                url("https://wwlolbcglcfhquyeenkn.supabase.co/storage/v1/object/public/public_assets/ThePeott.png") center/cover;
    border-radius: 10px;
    margin: 20px;
    height: 120px;
    padding: 16px;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.6);
    box-shadow: 0 4px 4px rgba(0, 0, 0, 0.1);
}

.team-sec h1 {
    font-size: 1.4rem;
    font-family: "Rubik", serif;
    font-optical-sizing: auto;
    font-weight: 600;
    font-style: normal;
}

.team-sec p {
    font-size: 0.7rem;
    font-family: "Rubik", serif;
    font-optical-sizing: auto;
    font-weight: 600;
    font-style: normal;
    padding-left: 10px;
}
</style>
