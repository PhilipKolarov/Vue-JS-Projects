<script>
    export default {
        props:{
            product:{
                type: Object,
                required: true,
                default:()=>({
                    id: -1,
                    title: 'NIGHT SUIT',
                    description: 'NIGHT SUIT DEFAULT',
                    price: 1,
                    discountPercentage: 0,
                    rating: 0,
                    stock: 0,
                    brand: 'DEFAULTS',
                    category: 'womens-dresses',
                    thumbnail: 'https://i.dummyjson.com/data/products/41/thumbnail/webp',
                    images: [
                        'https://i.dummyjson.com/data/products/41/1.jpg',
                    ]
                })
            },
        },
    };
</script>

<template>
    <article>
        <img :src="product.thumbnail" alt="img">
        <h2>{{ product.title }}</h2>
        <p>
          {{product.description}}
        </p>
        <p><b>Price</b>: {{product.price}}$</p>
        <footer>
          <button class="secondary outline">
            Add to cart 🛒
          </button>
        </footer>
    </article>
</template>

<style scoped>

</style>