<script setup>
    import Cart from './Card.vue'
    
    defineProps({
        items: Array
    })

    const onClickAdd = () => {
        alert('Добавить')
    }
</script>


<template>

    <div class="grid grid-cols-4 gap-5">
        <Cart 
            v-for="item in items"
            v-key="item.id"
            :title="item.title" 
            :imageUrl="item.imageUrl" 
            :price="item.price"/>
            :onClickAdd="onClickAdd"
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
        <Cart />
    </div>

</template>