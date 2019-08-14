<template>
    <div class="nav"> 
        <b-navbar variant="faded" type="light">
            <b-navbar-brand href="#">
            <img src="https://placekitten.com/g/30/30" alt="Kitten">
            MyBlog
            </b-navbar-brand>
            <b-nav-item > <nuxt-link to="/app-page/home">Home</nuxt-link></b-nav-item>
            <b-nav-item> <nuxt-link to="/navLink">Link</nuxt-link></b-nav-item>
            <b-nav-item> <nuxt-link to="/app-page/contact">Contact</nuxt-link></b-nav-item>
            <b-nav-item ><nuxt-link to="/about">About</nuxt-link></b-nav-item>
            <b-nav-item> <nuxt-link to="/app-page/info-page">Add Infomation</nuxt-link></b-nav-item>
        </b-navbar>
    </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
