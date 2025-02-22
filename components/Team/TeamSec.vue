<script setup>
const memberCount = ref(200);
</script>

<template>
    <div class="team-sec-container">
        <div class="team-sec-banner">
            <img src="https://wwlolbcglcfhquyeenkn.supabase.co/storage/v1/object/public/public_assets/ThePeott.png" alt="">
        </div>
        <div class="team-sec-details">
            <h1>TeamName</h1>
            <p id="team-sec-memeber-count">{{ memberCount }} members</p>
        </div>
    </div>
</template>

<style scoped>
.team-sec-container {
    display: flex;
    flex-direction: column;
    background-color: #f5f5f5;
    border-radius: 10px;
    margin: 20px;
    overflow: hidden;
    box-shadow: 0 4px 4px rgba(0, 0, 0, 0.1);
}

.team-sec-banner img {
    width: 100%;
    max-height: 200px;
    object-fit: cover;  
}

.team-sec-details {
    padding: 20px;
}

.team-sec-details h1 {
    font-size: 1.6rem;
    font-family: "Rubik", serif;
    font-optical-sizing: auto;
    font-weight: 600;
    font-style: normal;
    padding-bottom: 4px;
}

.team-sec-details p {
    font-size: 0.8rem;
    font-family: "Rubik", serif;
    font-optical-sizing: auto;
    font-weight: 600;
    font-style: normal;
    padding-left: 10px;
}
</style>