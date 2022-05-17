<template>

    <header class="container-fluid">

      <div id="logo">
        LOGO
      </div>

      <div class="gender">
        <select name="" id="">
          <option value="">Seleziona un genere</option>
        </select>
      </div>

    </header>

</template>

<script>
export default {
  name: 'HeaderComponent'
}
</script>

<style lang="scss" scoped>

@import '../assets/style/var';


  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: (lighten($primary-color, 5%));
    height: 70px;
    position: fixed;
    top: 0;
    z-index: 999;

    select{
      padding: 5px;
    }
  }

</style>