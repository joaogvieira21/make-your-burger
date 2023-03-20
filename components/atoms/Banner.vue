<template>
    <div id="main-banner">
        <h1>Make Your Burger!</h1>
    </div>
</template>

<script>
    export default {
        name:"Banner"
    }
</script>

<style>
    #main-banner {
        background-image: url('/img/burger.jpg');
        background-position: 0 -350px;
        background-size: cover;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        background-repeat: no-repeat;
        background-size: 100% 130%;
    }

    #main-banner h1 {
        color:white;
        font-family: Arial, Helvetica, sans-serif;
        font-size: 5rem;
        margin: 0 5% 10%

    }
</style>