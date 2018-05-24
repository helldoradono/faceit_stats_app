<template>
    <div class="py-5 text-center">
      <div class="container">
        <div class="row">
          <div class="col-12">
            <h1 class="display-3 text-capitalize">Sign In</h1>
            <div class="row">
              <div class="col-3"></div>
              <div class="col-6">
                <p class="lead text-muted">To get Started Please Login.</p>
                  <input type="text" v-model="email" class="form-control" placeholder="Enter email"><br>
                  <input type="password" v-model="password" class="form-control" placeholder="Password"><br>
                  <button class="btn btn-primary m-2" v-on:click="signIn"><i class="fas fa-sign-in-alt"></i> Login</button>
                <p>You don't have an account ? You can <router-link to="/sign-up">create one</router-link></p>
              </div>
              <div class="col-3"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>  
  import firebase from 'firebase'
  
  export default {
    name: 'login',  
    data () {
      return {
        email: '',
        password: ''            
      }      
    },
    methods: {
      signIn: function() {
        firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
          (user) => {
            this.$router.replace('home');
            this.$localStorage.set('isLoggedin', true);
          },
          (err) => {
            alert('Oops. ' + err.message)
          }
        );
      }  
    }
  }
</script>

<style scoped></style>