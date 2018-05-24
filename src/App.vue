<template>
  <body>
    <div id="app"> 
      <navbar></navbar>        
        <preview :userstatic=userstatic></preview>
        <router-view></router-view>
    </div>
  </body>
</template>

<script>
import Navbar from './components/Navigation.vue';
import Preview from './components/Preview.vue';

export default {     
  name: 'App',
  components: { Navbar, Preview },
  data () {
    return {
      userstatic: [],      
    }
  },
  created () {
    fetch('http://localhost:3000/db')
    .then((res) => { return res.json() } )
    .then((res) => { this.userstatic = res.data; })
  } 
}
</script>

<style>
 @import '../theme.css';
 @import 'https://use.fontawesome.com/releases/v5.0.13/css/all.css';
</style>
