<script setup>
    import Cart from './Card.vue'
    
    const onClickAdd = () => {
        alert('Добавить')
    }
</script>


<template>

    <div class="grid grid-cols-4 gap-5">
        <Cart 
            title="Мужские Кроссовки Nike Blazzer Mid Suede" 
            imageUrl="/sneakers/sneaker-1.jpg" 
            :price="12999"/>
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