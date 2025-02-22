<script setup>
import NoTeam from '~/components/Team/NoTeam.vue';
import TeamSec from '~/components/Team/TeamSec.vue';

const hasTeam = ref(true);
</script>

<template>
  <NuxtLayout>
    <TeamSec v-if="hasTeam"/>
    <NoTeam v-else />
  </NuxtLayout>
</template>
