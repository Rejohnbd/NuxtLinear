<template>
<div>
    <button 
        class="text-sm bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-2 rounded-full mb-4"
        @click="$fetch"
    >
        Refresh
    </button>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occured.</p>
    <div 
        v-for="product in products"
        v-else
        :key="product.title" 
        class="mb-4 flex felx-col text-let md:flex"
    >
        <div class="md:flex-shrink-0">
            <img class="rounded-lg md:w-56" :src="product.image" :alt="product.title" />
        </div>
        <div class="mt-4 md:mt-0 md:ml-6">
            <div class="uppercase tracking-wide text-sm text-indigo-500 font-bold">
                {{ product.continent }}
            </div>
            <NuxtLink 
                :to="product.slug"
                class="block mt-1 text-lg leading-tight font-semibold text-gray-900 hover:underline">
                {{ product.title }}
            </NuxtLink>
            <p class="mt-2 text-gray-600">
                {{ product.description }}
            </p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            products: []
        }
    },
    async fetch() {
        this.products = await fetch(
            'https://api.nuxtjs.dev/mountains'
        ).then(res => res.json())
    },
}
</script>

<style lang="postcss">
img {
    height: 120px;
}
</style>
