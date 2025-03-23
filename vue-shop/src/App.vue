<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios';

import Header from './components/Header.vue';
import CartList from './components/CartList.vue';

const items = ref([]);

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}

const fetchFavorites = async () => {
  try {
    const { data:favorites } = await axios.get('https://a45c28cb6fcb8ca4.mokky.dev/favorites')

    items.value = items.value.map(item =>{
      const favorite = favorites.find(favorite => favorite.id === item.id)

      if (!favorite) {
        return item;
      }

      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }

    })
  } catch (err) {
    console.log(err)
  }
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const { data } = await axios.get('https://a45c28cb6fcb8ca4.mokky.dev/items', {
      params
    })

    items.value = data.map(obj => ({
      ...obj,
      isFavorite: false,
      isAdded: false
    }));
  } catch (err) {
    console.log(err)
  }
}

// onMounted(async () => {
  await fetchItems();
  await fetchFavorites();
// }

onMounted(async () => {
  console.log('onMounted hook triggered');
  try {
    console.log('Fetching data from API...');
    const { data } = await axios.get('https://a45c28cb6fcb8ca4.mokky.dev/items');
    console.log('Data received:', data);
    items.value = data;
  } catch (err) {
    console.error('Error fetching data:', err);
  }
});

</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все товары</h2>

        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none">
            <option>По названию</option>
            <option>По цене (Дешёвые)</option>
            <option>По цене (Дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="search">
            <input class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400" type="text" placeholder="Поиск..." />
          </div>
        </div>
      </div>
      <div class="mt-10">
          <CartList :items="items" />
        </div>
    </div>
  </div>
</template>