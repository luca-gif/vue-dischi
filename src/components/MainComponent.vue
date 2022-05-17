<template>
  <main>
    <div class="container-fluid">
      <div class="container">
        <div class="row row-cols-5 py-5">

          <div v-for="(data, index) in datas" :key="index" class="col-2 card text-center p-3 m-3">
            <img :src="data.poster" :alt="data.title">

            <h5>{{data.author}}</h5>
            <p>{{data.year}}</p>
          </div>
          
        </div>
      </div>
    </div>
  </main>
</template>

<script>

import axios from 'axios';

export default {
  name: 'MainComponent',
  data(){
    return{
      url: 'https://flynn.boolean.careers/exercises/api/array/music',
      datas: [],
    }
  },

  methods: {
    getApi(){
      axios.get(this.url)
      .then(r=>{
        this.datas = r.data.response;
        console.log(this.datas);
      })
    }

  },
  mounted(){
    this.getApi()
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/var';

  main{
    min-height: calc(100vh - 70px);
    background-color: $primary-color;

    .card{
      background-color: (lighten($primary-color, 5%));
    }
  }

</style>