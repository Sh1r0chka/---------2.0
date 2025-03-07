<template>
    <header class="flex justify-between border-b border-slate-100 px-10 py-10">
        <div class="flex item-center gap-4">
            <img src="/logo.png" alt="logo" class="w-12 h-13" />
            <div>
                <h2 class="text-xl font-bold uppercase">VUE КЕДЫ</h2>
                <p class="text-slate-400">Магазин лучших кроссовок</p>
            </div>
        </div>

        <ul class="flex items-center gap-10">
            <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
                <img src="/heart.svg" alt="heart">
                <span>Закладки</span>
            </li>

            <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
                <img src="/profile.svg" alt="profile">
                <span>Профиль</span>
            </li>
        </ul>
    </header>
</template>