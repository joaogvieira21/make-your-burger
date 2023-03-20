<template>
    <Navbar></Navbar>
        <slot />
    <Footer class="footer"></Footer>
</template>

<script>
    import Navbar from '../components/organisms/Navbar.vue'
    import Footer from '../components/organisms/Footer.vue'
    
    export default {
        
        components: {
            Navbar,
            Footer,
        }
    }

</script>

<style scoped>
    .footer {
        position: absolute;
        bottom: 0px;
        width:100%;
    }

</style>