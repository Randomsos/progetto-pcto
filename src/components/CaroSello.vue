<template>
  <div class="container" v-if="top3">
    <div class="row">
      <div class="col-6 destra">
      <br>
      <br>
      <div class="black-background">
        <h1 class="paragrafi">I FILM E LE SERIE CHE PIU' AMATE A DISTANZA DI UN CLICK</h1>
      </div>
        <div class="targhetta"> 
         <h4> Guarda e condividi le serie e i tuoi film preferiti con le persone che più ami </h4>
        </div>
     </div>
        <div class="col-6">
        <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel-indicators">
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
      <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
    </div>
    <div class="carousel-inner">
      <div class="carousel-item" v-for="(img, index) in top3" :key="index" :class="{'active' : index === 0}">
        <img :src= "getImage(img.poster_path)" class="car-img d-block w-100" alt="...">
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
      </div>
    </div>
  </div> 
</template>

<script>
    export default {
      name: 'carouselComponent',
       props: {
            top3: {
                type: Object,
                default: () => {
                    return {
                      results: []
                    }
                }
            },
        },
      methods:{
        getImage(posterPath){
          return 'https://image.tmdb.org/t/p/original' + posterPath
        }
      }
  }
</script>
