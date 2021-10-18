<template>
    <div>
        <Navbar/>
        <h1>This is my home page</h1>
        <img src="../assets/logos/logo.png" alt="">
        <Footer/>
    </div>
</template>

<script>
import Navbar from '../components/Navbar.vue'
import Footer from '../components/Footer.vue'
    export default {
        components:{
            Navbar,
            Footer
        }
    }
</script>

<style lang="scss" scoped>

</style>