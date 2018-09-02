<template>
  <div class="wrapper">
    <Claim />
    <SearchInput />
  </div>
</template>

<script>
import axios from 'axios';

import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'App',
  components: {
    Claim,
    SearchInput,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
      handleInput: debounce(function() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }

  body {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100vh;
    margin: 0;
    padding: 30px;
    justify-content: center;
    background-image: url('assets/heroimage.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 80% 0%;
  }
</style>
