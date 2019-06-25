<template>
   <div :class="[{ flexStart: step ===1 }, 'wrapper']">
       <transition name="slide">
           <img src="../../assets/logo.svg" class="logo" alt="" v-if="step === 1">
       </transition>
       <transition name="fade">
       <HeroImage v-if="step === 0"/>
       </transition>
       <Claim  v-if="step === 0"/>
        <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
   </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'Search',
  components: {
    HeroImage,
    Claim,
    SearchInput,
  },
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      this.loading = true;
      console.log(this.searchValue);
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        }).catch((error) => {
          console.log(error);
        });
    }, 500),

  },
};

</script>

<style lang="scss" scoped>
    .fade-enter-active, .fade-leave-active {
        transition: opacity .3s ease;
    }
    .fade-enter, .fade-leave-tp {
        opacity: 0;
    }

    .slide-enter-active, .slide-leave-active {
        transition: margin-top .5s .3s ease;
    }
    .slide-enter, .slide-leave-tp {
        margin-top: -100px;
    }

    li  {
        list-style-image: url("");
    }
    .wrapper {
        position: relative;
        display: flex;
        flex-direction: column;
        padding: 30px;
        align-items: center;
        justify-content: center;
        margin: 0;
        width: 100%;
        height: 100vh;
        top: 0;
    }
    .flexStart {
        justify-content: flex-start;
    }

    .logo {
        position: absolute;
        top: 30px;
        max-width: 50px;
        height: auto;
    }

</style>
