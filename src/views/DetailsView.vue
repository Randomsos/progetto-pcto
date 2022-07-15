<template>
    <div class="container">
        <div class="row">
          <ul class="descrizione">
              <li>{{dettagli.name}} </li>
              <li>Numero stagioni: {{dettagli.number_of_seasons}}</li>
              <li>Numero episodi: {{dettagli.number_of_episodes}}</li>
              <li>Durata media episodi: {{dettagli.episode_run_time}}</li>
              <li>Attualmente visibile su: 
              
                <span v-for="network in dettagli.networks" :key="network.id">
                {{network.name}} <br>
                 <img class="logo" :src="getImage(network.logo_path)"/>
                </span>
               
                </li>
              <li>Lingura orginale: {{dettagli.original_language}}</li>
              <li>Media voti: {{dettagli.vote_average}}</li>
              <li>Uscito per la prima volta nel: {{}}</li>
            </ul>

            <p class="targhetta">{{dettagli.overview}}</p>
            </div>
            <div class="row">
              <img class="details-img" :src="getImage(dettagli.backdrop_path)">
            </div>
        </div>
</template>

<script>
    export default {
      data(){ 
        return{
            dettagli: {
              seasons: []
            },
            id: this.$route.params.id,
            lingua: this.$route.params.lingua
        }        
      },
      created(){
      this.getData()
      },
      methods:{
        getData(){
            fetch('https://api.themoviedb.org/3/tv/' + this.id + '?api_key=6f9286d54de4891ea7a5c91779e09786&language=' + this.lingua)
            .then(res => res.json())
            .then(data => this.dettagli = data)
            .then(console.log(this.dettagli))
        },
        getImage(posterPath){
          return 'https://image.tmdb.org/t/p/original' + posterPath
        },
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
      
  }
</script>
