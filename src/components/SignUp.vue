<template>
    <div class="py-5 text-center">
      <div class="container">
        <div class="row">
          <div class="col-12">
            <h1 class="display-3 text-capitalize">Sign Up</h1>
            <div class="row">
              <div class="col-3"></div>
              <div class="col-6">
                <p class="lead text-muted">To get Started Please SignUp.</p>
                  <input type="text" v-model="email" class="form-control" placeholder="Enter email"><br>
                  <input type="password" v-model="password" class="form-control" placeholder="Password"><br>
                  <button class="btn btn-primary m-2" v-on:click="signUp">Register</button>
                <p>Or go back to <router-link to="/login">Login</router-link></p>
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
    name: 'signUp',
    data: function() {
      return {
        email: '',
        password: ''
      }
    },
    methods: {
      signUp: function() {
        firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
          (user) => {
            this.$router.replace('home')
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