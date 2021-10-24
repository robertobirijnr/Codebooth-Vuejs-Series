<template>
    <header id="main-header" class="bg-danger text-white p-4 mb-3">
      <div class="container">
        <h1 id="header-title">{{title}}</h1>
      </div>
    </header>
</template>

<script>
    export default {
        name:"Navbar",
        data() {
            return {
                title: "Vue Todo App"
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>