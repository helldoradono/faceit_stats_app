<template>
    <div class="pres">        
        <div class="footer">
            <div class="surgu">
                <div v-for="(usersta, itam) in userstatic" :key="itam" class="lastwinscpanel">
                    <div>
                      <img :src="usersta.payload.avatar" class="classplayeravatar"> 
                      <p class="elo-under">{{usersta.payload.games.csgo.faceit_elo}}</p>
                    </div>
                </div>																		
            </div>
          </div>
        <div class="foot">
          <div class="container">
            Made by Helldorado with Vue.JS - 2018
          </div>
        </div>      
    </div>
</template>

<script>
export default {   
   props: [ 'userstatic' ]
};
</script>

<style scoped>
@import '../../preview.css';
</style>

