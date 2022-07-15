<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#"><span class="imp">{{titolo}}</span></a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link to="/"> <a class="nav-link active" aria-current="page" href="#">Home</a></router-link>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Scegli la lingua</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            {{lingua1}}
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#" @click="changeLing">{{lingua2}}</a></li>
          </ul>
          
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Scegli Genere</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            {{genere1}}
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#" @click="changeGen">{{genere2}}</a></li>
          </ul>
          
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">Disabled</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
  <!-- <router-link to="/dettagli"> essendo che </router-link>-->
  <router-view></router-view>
</template>
<script>
    export default {
        data() {
            return {
                linguaUrl:'',
                lingua: true,
                genere: true,
                titolo: 'Film&Series',
                top3: [],
            }
        },

        methods: {
          changeGen(){
            this.genere = !this.genere
            const query = this.genere ? 'serie tv' : 'films'
            this.$router.push({ query: {gen: query}})
            /*if(this.genere){
            this.linguaUrl = 'serie tv'
            }
            else{
              this.linguaUrl = 'films'
            }*/
          },
          changeLing() {
            this.lingua = !this.lingua
            const query = this.lingua ? 'it-IT' : 'en-EN'
            this.$router.replace({ query: {lang: query}})
            if(this.lingua){
            this.linguaUrl = 'it-IT'
            }
            else{
              this.linguaUrl = 'en-US'
            }
          }
        },

        computed: {
           
           switchLingua(){
              return this.setURL
           },
           lingua1 () {
                 
            if (this.lingua==true) 
            {
                return "italiano"    
            }
            else
            {
                return "inglese"
            } 
            },
             lingua2() {
                if (this.lingua==true) {
                    return "inglese"    
                }
                else{
                    return "italiano"
                }
            },
            genere1 () {
                 
            if (this.genere==true) 
            {
                return "serie tv"    
            }
            else
            {
                return "films"
            } 
            },
             genere2() {
                if (this.genere==true) {
                    return "film"    
                }
                else{
                    return "serie tv"
                }
            }
        },
        
    }

</script>
<style> 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

@import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;1,100&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;1,100&family=Source+Sans+Pro:wght@200&display=swap');
body {
  background-image: url(./assets/backgroud.jpg);
  background-repeat: no-repeat;
  margin: 0px;
  background-attachment: fixed; 
  font-family: tahoma;
  color: #282828;
}
.buttoni-next{
  margin: auto;
  height: 30px;
}

.font-20{
  font-size: 18px;
}
.bottoni:hover{
  background-color: rgb(255, 117, 93) !important;
}

.bottoni2{
  margin: right !important;
  background-color: whitesmoke !important;
  color: black !important;
}

.bottoni{
  margin: left !important;
  margin: bottom !important;
  margin: top !important;
  background-color:#f00212 !important;
  border-width: 0px !important;
}
.targhetta{
  border-width: 5px;
  font-family: 'Lato', sans-serif;
  font-family: 'Source Sans Pro', sans-serif;
  background-color: whitesmoke;
  border-style: double;
}
.sas{
  float: left !important;
  margin: left !important;
  margin-top: 50px !important;
  height: 535px !important;
  font-family: 'Lato', sans-serif !important;
  font-family: 'Source Sans Pro', sans-serif !important;
  background-color: #282828 !important;
  color: whitesmoke !important;

}
.accentramento {
   margin: auto;
   border-width: 0px;
  }

.black-background{
  background-color: #282828;
}
.destra {
  text-align: right;
}
.paragrafi{
  color: whitesmoke;
  font-family: 'Lato', sans-serif;
}
.imp {

  color: #f00212;
  font-family: 'Lato', sans-serif;

}

h1 {
  font-size: 50px;
}

h3 {
  font-size: 25px;
}
.logo{
  width: 80px;
  height: 25px;
}
.descrizione{
  text-align: left;
  color: whitesmoke;
  font-family: 'Lato', sans-serif;
  font-family: 'Source Sans Pro', sans-serif;

}
.details-img{
  border: 2px solid #d8d8d8;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 2px 15px -12px rgba(0, 0, 0, 0.57);
  margin: auto;
  border-width: 0px;
}
.car-img {
  border: 2px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  padding: 15px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 2px 15px -12px rgba(0, 0, 0, 0.57);
  margin: auto;
  border-width: 0px;
}

.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 25px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.57);
}

p {
  font-size: 22px;
}

ul {
  list-style-type: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
