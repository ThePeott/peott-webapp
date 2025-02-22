<script setup>
import HeadP from '~/layouts/FootP.vue'
import FootP from '~/layouts/HeadP.vue'
</script>

<template>
    <div>
        <HeadP />
        <slot />
        <FootP />
    </div>
</template>