<template>
  <div>
    <Navbar/>
  <div class="main-container">
  <div class="content">
    <keep-alive>
    <router-view/>
    </keep-alive>
     </div>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Footer from '../components/Main/Footer.vue'
import Navbar from '../components/Main/Navbar.vue'
export default {
  name: 'main',
  components: {
    Navbar,
    Footer
  },
  mounted () {
    console.log('main is mounted')
    console.log(localStorage.getItem('token'))
    if (localStorage.getItem('token') === null) {
      if (localStorage.getItem('oauthID') === null) {
        this.$router.push({ name: 'signin' })
      }
    } else if (localStorage.getItem('oauthID') === null) {
      if (localStorage.getItem('token') === null) {
        this.$router.push({ name: 'signin' })
      }
    }
  }
}
</script>

<style>
.main-container
{
background-color: #d7e5f3;
  height: 100vh;

}
.main-container .content
{
  padding-top: 4.1rem;
  padding-bottom: 3.5rem;
}
</style>
