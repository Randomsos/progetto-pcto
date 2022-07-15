<template>
  <div class="container">
    <br>
    <br>
      <div class="row">
         <h3 class="paragrafi">Benevenuti nel catalogo di film, anime e serie TV: <span class="imp">"{{titolo}}"</span> </h3>       
      </div>
  </div>
      <car :top3="top3"/>
      <card :series="series"/>
    
</template>

<script>
import car from '../components/CaroSello.vue'
import card from '../components/CardComp.vue';
export default {
    components:{
      car, card
    },
  data() {
    return {
      titolo: 'Film&Series',
      series: [],
      top3: [],
      lingua: 'it-IT',
      gen: this.$route.params.genere
    }
  },
  methods: {
    //if(genere){}
     getData(){
        fetch('https://api.themoviedb.org/3/tv/top_rated?api_key=6f9286d54de4891ea7a5c91779e09786&language=' + this.lingua + '&page=1')
        .then(res => res.json())
        .then(data => {
          this.series = data
          this.top3 = data.results.slice(0,3)
          })
      //else{}
        /* fetch('https://api.themoviedb.org/3/movie/top_rated?api_key=6f9286d54de4891ea7a5c91779e09786&language=' + this.lingua + '&page=1')
        .then(res => res.json())
        .then(data => {
          this.series = data
          this.top3 = data.results.slice(0,3)
        }) */

      }
  },
  watch: {
      '$route.query.lang': {
          handler: function(language) {
              this.lingua = language
              this.getData()
          
          },
          deep: true,
          immediate: true
      }
  },
  created() {
    this.getData()
  }
}
</script>
