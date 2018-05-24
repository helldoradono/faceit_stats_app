<template>
    <div class="container">        
        <div class="py-5 text-center">
          <div class="container">
            <div class="row">
              <div class="col-12">
                <h1 class="display-3 text-capitalize">Faceit Stats</h1>
                <div class="row">
                  <div class="col-3"></div>
                  <div class="col-6">
                    <p class="lead text-muted">Get your Advanced Statics with 1 click.</p>
                    <input type="text" class="search-query form-control" 
                    placeholder="faceit-username" v-model="query" @keypress.enter="search" />
                    <div v-if="isLoading" class="text-center sk-folding-cube">
                      <div class="sk-cube1 sk-cube"></div>
                      <div class="sk-cube2 sk-cube"></div>
                      <div class="sk-cube4 sk-cube"></div>
                      <div class="sk-cube3 sk-cube"></div>
                    </div>  
                  </div>
                  <div class="col-3"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
       <div class="lds-ripple" v-if="isLoading"><div></div><div></div></div>         
        <div class="py-5">
          <div class="container">
            <div class="row">    
              <div class="col-md-12" style="">               
              </div>
            </div>
          </div>
        </div>

        <div class="py-5">
          <div class="container">
            <div class="row">    
              <div class="col-md-12" style=""> 
                <div v-if="result">            
                  <p>{{ reversedMessage }}</p>
                  <div class="backii">
                    <div>
                        <img class="uzer-img" :src="result.payload.avatar" />
                      </div>
                      <p class="user-dats">            
                        {{ result.payload.games.csgo.faceit_elo }}
                      </p>
                      <p>{{ result.payload.nickname }}</p>
                      <div v-if="result.payload.games.csgo.skill_level_label == '1'">
                        <img class="level-img" src="/static/img/skill_level_1_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '2'">
                        <img class="level-img" src="/static/img/skill_level_2_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '3'">
                        <img class="level-img" src="/static/img/skill_level_3_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '4'">
                        <img class="level-img" src="/static/img/skill_level_4_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '5'">
                        <img class="level-img" src="/static/img/skill_level_5_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '6'">
                        <img class="level-img" src="/static/img/skill_level_6_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '7'">
                        <img class="level-img" src="/static/img/skill_level_7_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '8'">
                        <img class="level-img" src="/static/img/skill_level_8_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '9'">
                        <img class="level-img" src="/static/img/skill_level_9_md.png" />
                      </div>
                      <div v-else-if="result.payload.games.csgo.skill_level_label === '10'">
                        <img class="level-img" src="/static/img/skill_level_10_md.png" />
                      </div>
                      <div v-else>
                        Not 1/2/3/4/5/6/7/8/9/10
                      </div>
                  </div>          
                </div>

              </div>
            </div>
          </div>
        </div>





        <h1 v-if="!tableLoading" class="h1yirmi">Last 5 Match</h1> 
        <table class="table">
          <thead v-if="!tableLoading">
            <tr>              
              <th scope="col">Link</th>
              <th scope="col">Team</th>
              <th scope="col">Elo</th>
              <th scope="col">K-A-D</th>
              <th scope="col">Score</th>
              <th scope="col">Map</th>              
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in userdata" :key="index">              
              <td><a target="_blank" v-bind:href="'https://www.faceit.com/en/csgo/room/' +item.matchId">
              <i class="fas fa-link"></i></a></td>
              <td class="team-name">{{ item.i5 }}</td>
              <td>{{ item.elo }}</td>
              <td>{{ item.i6 }}-{{ item.i7 }}-{{ item.c4 }}</td>
              <td>{{ item.i18 }}</td>
              <td>{{ item.i1 }}</td>
            </tr>
          </tbody>
        </table>
    </div>      
</template>

<script>
export default {  
  data() {
    return {
      query: '',
      isLoading: false,
      tableLoading: true,
      result: false,
      userdata: false,
      userpata: false,       
    };
  },
  methods: {    
    search() {
      fetch(`https://api.faceit.com/api/nicknames/${this.query}`)
        .then(result => result.json())
        .then((result) => {
          this.result = result;          
          this.isLoading = true;
          this.tableLoading = false;
          this.$localStorage.set('userdetails', JSON.stringify(this.result));          
        });        
    },
  },
  computed: {
    reversedMessage() {
      fetch(`https://api.faceit.com/stats/api/v1/stats/time/users/${this.result.payload.guid}/games/csgo?page=0&size=5`)
        .then(userdata => userdata.json())
        .then((userdata) => {                   
          this.userdata = userdata;          
          this.$localStorage.set('matches', JSON.stringify(this.userdata));          
          this.isLoading = false;
        });        
    }
  }
};
</script>

<style scoped>
@import '../../search.css';
</style>

