<template>
  <div v-if="product">
    <img :src="product.img_url" :alt="product.title">
    <h2>{{ product.title }}</h2>
    <p>{{ product.description }}</p>
  </div>
  <div v-else>Loading...</div>
</template>

<script>
export default {
    props: ["id"],
    data(){
        return{
            product: null
        }
    },
    mounted(){
        fetch("http://localhost:3000/products/" + this.id)
        .then(res => res.json())
        .then(data => this.product = data)
    }
}
</script>

<style>

</style>