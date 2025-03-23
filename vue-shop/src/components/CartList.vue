<script setup>
    import CartItem from './CartItem.vue'
    
    defineProps({
        items: Array
    })

    const onClickAdd = () => {
        alert('Добавить')
    }
</script>

<template>
    <div class="grid grid-cols-4 gap-5" v-auto-animate>
        <CartItem
            v-for="item in items"
            :key="item.id"
            :title="item.title" 
            :imageUrl="item.imageUrl" 
            :price="item.price"
            :onClickAdd="onClickAdd" 
            isFavorite=""
        />
    </div>
</template>