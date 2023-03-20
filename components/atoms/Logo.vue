<template>
    <img :src="logo" :alt="alt">
</template>

<script>
    export default {
        name:"Logo",
        data() {
            return {
                logo:'./img/logo.png',
                alt: 'logo-burger'
            }
        }
    }
</script>