<template>
  <div id="app">
    <Navbar />
    <router-view />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
export default {
  components: {
    Navbar,
  },
  //  beforeCreate(){
  //   alert("Before Created")
  // },
  // created(){
  //   alert("Created")
  // },
  // beforeMount(){
  //   alert("Before Mounted")
  // },
  // mounted(){
  //   alert("Mounted")
  // }
};
</script>

<style></style>
