<template>
  <router-link :to="{ name: 'product', params: {id: product.id} }" class="card">
    <img :src="product.img_url" :alt="product.title">
    {{ product.title }}
  </router-link>
    <button @click="() => editMe(product.id)">Edit me</button>
</template>

<script>
export default {
    props: ['product'],
    methods: {
        editMe(id) {
            fetch('http://localhost:3000/products/' + id, {
                method: 'PUT',
                body: JSON.stringify({
                    title: 'Cheap Change',
                    price: 0.01,
                    img_url: "https://picsum.photos/600?random=1",
                    description: "This was changed, now its cheap",
                    category: "change",
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