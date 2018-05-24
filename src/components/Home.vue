<template>
    <div class="py-5">
      <div class="container">
        <div class="row">
          <div class="col-md-12"> 
            <search></search>          
            <button class="btn btn-primary m2 left-up-static" v-on:click="logout"><i class="fas fa-sign-out-alt"></i> Logout</button>            
          </div>
        </div>
      </div>
    </div> 
</template>

<script>
import firebase from 'firebase'
import Search from './Search';

export default {
  name: 'home',
  components: { Search },
  data () {
    return {}
  },   
  methods: {
    logout: function() {
      firebase.auth().signOut().then(() => {
        this.$router.replace('login')
        this.$localStorage.set('isLoggedin', false);
      })
    }
  }
}
</script>

<style scoped>
.left-up-static {
  position: fixed;
  top: 10px;
  right: 8px;
  background: #bb0c0ccc;
  color: white;
  font-size: 13px;
  font-weight: 400;
}
</style>