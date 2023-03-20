<template>
  <Banner></Banner>
  <BurgerForm></BurgerForm>
  <Footer></Footer>
</template>

<script>
  import Banner from '~~/components/atoms/Banner.vue';
  import BurgerForm from '~~/components/molecules/BurgerForm.vue'
  import Footer from '~~/components/organisms/Footer.vue';
  export default {
    name:"index",
    components: {
      Banner,
      BurgerForm,
      Footer
    }
  }


</script>