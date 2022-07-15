<template>
<div class="container">
    <div class="row">
        <div class="col-4" v-for="serie in series.results" :key="serie.id">
            <div class="card sas" style="width: 14rem;">
                <img :src="getImages(serie.poster_path)" class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title">{{serie.name}}</h5>
                    <p class="card-text">primo episodio uscito nel: {{serie.first_air_date}}</p>
                    <router-link :to="{ name: 'dettagli', params: { id: serie.id }}"><a href="#" class="btn btn-primary bottoni">Go somewhere</a></router-link>
                    <!-- <router-link :to="{ name: 'dettagli', params: { id: serie.id }}"><a href="#" class="btn btn-primary bottoni">Go somewhere</a></router-link>-->
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script> 
    export default {

        props: {
            series: {
                type: Object,
                default: () => {
                    return {
                      results: []
                    }
                }
            },
        },
        methods: {
            
            getImages(poster_path){
            return "https://image.tmdb.org/t/p/original" + poster_path
            },
        },
    }
</script>