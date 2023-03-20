<template>
    <div class="logo-container">
        <Logo class="img"></Logo>
        <h1>BI Burger</h1>       
    </div>
</template>

<script>
    import Logo from '../atoms/Logo.vue'
    import MenuContainer from './MenuContainer.vue';
    export default {
        name:"LogoContainer",
        components: {
            Logo,
            MenuContainer
        } 
    }
    
</script>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Dangrek&family=Montserrat:wght@900&family=Open+Sans:wght@300;400&family=Oswald&family=Press+Start+2P&family=Quicksand:wght@300;400;500;600;700&family=Raleway:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,400;1,500;1,600;1,800;1,900&family=Roboto:ital,wght@1,500;1,700&display=swap');
    h1 {
        font-family: 'Press Start 2P';
        color: white;
        font-style: none;
        margin-top: 3px;
    }
    .img {
        position: relative;
        margin: 0 50px;
        
        
    }

  
</style>