<script setup>
import NoTeam from '~/components/Team/NoTeam.vue';
import TeamSec from '~/components/Team/TeamSec.vue';
import Coin from '~/components/Coin/Coin.vue';

const hasTeam = ref(true);
</script>

<template>
    <div class="container">
        <TeamSec v-if="hasTeam"/>
        <NoTeam v-else />
        <Coin enable/>
    </div>
</template>