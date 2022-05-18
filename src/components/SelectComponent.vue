<template>
  <div>
    <select v-model="selected" @change="$emit('changeValue', selected)" name="" id="">

       <option value="0">Seleziona un genere</option>
       <option value="1">Seleziona un genere</option>
       <option value="2">Seleziona un genere</option>

    </select>
  </div>
</template>

<script>
export default {
  name: 'SelectComponent',

  data(){
    return{
      selected: 0
    }
  }
}
</script>

<style>

</style>