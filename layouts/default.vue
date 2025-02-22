<script setup>
import HeadP from '~/layouts/HeadP.vue'
import FootP from '~/layouts/FootP.vue'
</script>

<template>
    <div>
        <HeadP />
        <slot />
        <FootP />
    </div>
</template>