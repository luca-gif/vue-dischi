<template>
  <div>
    <select v-model="selected" @change="cambioValore">

       <option disabled value="">Seleziona un genere</option>
       <option value="all">All</option>
       <option value="rock">Rock</option>
       <option value="pop">Pop</option>
       <option value="jazz">Jazz</option>
       <option value="metal">Metal</option>

    </select>
  </div>
</template>

<script>

export default {
  name: 'SelectComponent',

  data(){
    return{
      selected: ''
    }
  },
  
  methods:{
    cambioValore(){
      //console.log(this.selected);
      this.$emit('changeValue',this.selected);
    }
  }
}

</script>

<style lang="scss" scoped>

select{
  margin-right: 10px;
}

</style>