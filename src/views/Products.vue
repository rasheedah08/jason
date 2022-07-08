<template>
  <div v-if="products">
    <h2>Look through my wares</h2>
    <button @click="addProduct">Add Product</button>
    <div class="products-container">
        <ProductCard v-for="product of products"  :key="product.id" :product="product"/>
    </div>
  </div>
  <div v-else>Loading...</div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
export default {
    components: {ProductCard },
    data(){
        return {
          products: null
        }
    },
    mounted(){
        fetch("http://localhost:3000/products")
        .then(res => res.json())
        .then(data => this.products = data)
    },
    methods: {
        addProduct(){
            fetch('http://localhost:3000/products', {
                method: 'POST',
                body: JSON.stringify({
                    title: 'Jasons Brain',
                    price: 99999999,
                    img_url: "https://picsum.photos/600?random=7",
                    description: "Cannot Describe",
                    category: "weapon",
                }),
                headers: {
                    'Content-type': 'application/json; charset=UTF-8',
                },
                })
                .then((response) => response.json())
                .then((json) => console.log(json));
        }
    }
}
</script>

<style>

</style>