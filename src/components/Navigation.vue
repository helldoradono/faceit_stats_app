<template>    
    <nav class="navbar navbar-expand-md bg-primary navbar-dark">
      <div class="container">
        <a class="navbar-brand" href="#"><i class="fa d-inline fa-lg fa-cloud"></i><b> FaceitStats.io</b></a>
        <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbar2SupportedContent"> 
          <span class="navbar-toggler-icon"></span> 
        </button>
          <div class="collapse navbar-collapse text-center justify-content-end" id="navbar2SupportedContent">
            <ul class="navbar-nav"></ul>            
          </div>
      </div>
    </nav>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'Navigation',   
  data () {    
    return {}
  } 
}
</script>

<style scoped></style>
