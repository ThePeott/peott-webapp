<script setup>
import NoTeam from '~/components/Team/NoTeam.vue';
import TeamSec from '~/components/Team/TeamSec.vue';
import CoinSec from '~/components/Coin/CoinSec.vue';

const hasTeam = ref(true);
</script>

<template>
    <div class="container">
        <TeamSec v-if="hasTeam"/>
        <NoTeam v-else />
        <CoinSec enable/>
    </div>
</template>