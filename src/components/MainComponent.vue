<template>
  <main>
    <div class="container-fluid">

      <header>

        <div class="logo">LOGO</div>

        <div class="genre">

          <select-component @changeValue="selectedGenre"/>

        </div>

      </header>

      <div class="container">
        <div class="row py-5">

          <div v-for="(data, index) in getAlbumFiltrati" :key="index" class="col-2 card lm-card text-center p-3 m-3">
            <img :src="data.poster" :alt="data.title">
            <h6 class="text-white text-uppercase py-3">{{data.title}}</h6>
            <span>{{data.author}}</span>
            <span>{{data.year}}</span>
          </div>
          
        </div>
      </div>
    </div>

  </main>
</template>

<script>

import axios from 'axios';
import SelectComponent from './SelectComponent.vue';

export default {
  name: 'MainComponent',

  components: {
    SelectComponent
  },

  data(){
    return{
      url: 'https://flynn.boolean.careers/exercises/api/array/music',
      datas: [],
      genereScelto : 'all'
    }
  },

  methods: {
    getApi(){
      axios.get(this.url)
      .then(r=>{
        this.datas = r.data.response;
      })
    },
  
    selectedGenre(genereSelezionato){
      this.genereScelto = genereSelezionato;
      //console.log(genereSelezionato);
    },

  },

    computed: {

      getAlbumFiltrati() {

        let arrayFiltrato = [];

        for(var i = 0; i < this.datas.length; i++) {

          console.log(this.datas[i].genre.toLowerCase(), this.genereScelto.toLowerCase());

          if (this.datas[i].genre.toLowerCase() == this.genereScelto.toLowerCase()) {
            arrayFiltrato.push(this.datas[i]);
          } else if (this.genereScelto.toLowerCase() == 'all'){
            arrayFiltrato = this.datas
          }
        }

        return arrayFiltrato;
      }      
      
    },
    

  mounted(){
    this.getApi()
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/var';
@import '../assets/style/global';


  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: (lighten($primary-color, 5%));
    height: 60px;
  }

  main{
    min-height: 100vh;
    background-color: $primary-color;

    .card{
      background-color: (lighten($primary-color, 5%));
    }
    .lm-card{
      height: 350px
    }
    span{
      color: #767372;
    }
  }

</style>