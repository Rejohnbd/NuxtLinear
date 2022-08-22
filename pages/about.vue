<template>
    <div class="container">
        <h1>About</h1>
        <p v-if="$nuxt.isOffline">Opps, you are offline.</p>
        <p v-if="$nuxt.isOnline">Yeahhh, I am online.</p>
        <NuxtLink to="/">Home</NuxtLink>
        <ProductCard />
    </div>
</template>

<script>
export default {
    name: 'AboutPage',
}
</script>