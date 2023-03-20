<template>
    <div class="menu-container">
        <NuxtLink :to="{ name: 'index'}">Home</NuxtLink>
        <NuxtLink :to="{ name: 'pedidos'}">Pedidos</NuxtLink>     
    </div>
</template>

<script>
    export default {
        name:"MenuContainer",
    }
</script>

<style scoped>
    .menu-container {
        display: flex;
        gap: 13px;
    }
    a {
        text-decoration: none;
        color: goldenrod;
        font-weight: bolder;
        font-family:'Times New Roman', Times, serif;
        font-size: 2em;
        transition:1s;
    }
    a:hover {
        color: white;
    }



</style>