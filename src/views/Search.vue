<template>
   <div class="wrapper">
       <div class="search">
           <label for="search">Search</label>
           <input name="search" id="search" type="search" v-model="searchValue" @input="handleInput">
       </div>
       <ul>
           <li v-for="item in results" :key="item.data[0].nasa_id">
                {{ item.data[0].description}}
           </li>
       </ul>
   </div>
</template>

<script>
    import axios from 'axios';
    import debounce from 'lodash.debounce';
    const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        }).catch((error) => {
        console.log(error);
      });
    },500),

  },
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
