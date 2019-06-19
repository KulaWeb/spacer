<template>
   <div class="wrapper">
       <div class="search">
           <label for="search">Search</label>
           <input name="search" id="search" type="search">
       </div>
   </div>
</template>

<script>
export default {
  name: 'Search',
};
</script>

<style lang="scss" scoped>
  .wrapper {
      display: flex;
      flex-direction: column;
      padding: 30px;
      align-items: center;
      margin: 0;
  }

    .search {
        display: flex;
        flex-direction: column;
        width: 300px;
        label {
            font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
            font-size: 18px;
        }
        input {
            border: 0;
            border-bottom: 2px solid black;
            height: 30px;
        }
    }

</style>
