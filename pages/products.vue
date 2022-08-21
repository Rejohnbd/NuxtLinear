<template>
    <div class="container mx-auto mt-8">
        <!-- <ProductCard :product="product" /> -->
        <ProductCard 
            v-for="product in products" 
            :key="product.title" 
            :product="product" 
            class="mb-4"
        />
    </div>
</template>

<script>

    export default {
        name: 'ProductsPage',
        data() {
            return {
                // product: {
                //     title: 'title',
                //     image: 'icon.png',
                //     description: 'description',
                //     continent: 'continent',
                //     slug: '/'
                // }
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

