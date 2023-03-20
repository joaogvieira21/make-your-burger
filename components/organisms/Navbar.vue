<template>
    <nav>
        <LogoContainer class="img"></LogoContainer>
        <div class="links">
            <MenuContainer></MenuContainer>
        </div>
    </nav>
</template>

<script>
    import LogoContainer from '../molecules/LogoContainer.vue';
    import MenuContainer from '../molecules/MenuContainer.vue';
    export default {
        name: "Navbar",
        components: {
            LogoContainer,
            MenuContainer
        },
        data() {
            return {
               
            }
        }
    }
</script>

<style scoped>
    nav {
        background-color: rgb(34, 32, 32);
        height: 19vh;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        border-bottom: 4px solid #111;
    }

    .links {
        display: flex;
        gap: 10px;
        text-transform: uppercase;
    }

    a {
        color: white;
        text-decoration: none;
        transition: 1s;
        font-weight: bolder;
    }
    a:hover {
        color: red;
    }


</style>