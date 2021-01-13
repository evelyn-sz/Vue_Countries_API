<template lang='html'>
  <div class='main-container'>
    <label for="country-select">Select Country</label>
      <select v-model="selectedCountry">
        <option disabled value="">Select country</option>
        <option v-for="country in countries">{{ country.name }}</option>
     </select>

     <countries-list :countries="countries"></countries-list>
     <country-detail :country="selectedCountry"></country-detail>
  </div>  
</template>

<script>

import { eventBus } from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import ListItem from './components/ListItem.vue';

export default {
  name: "app",
  data () {
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      // console.log('within $on, country');
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,
    "list-item": ListItem
  }
}
</script>




<style>

  .main-container {
    display: flex;
    justify-content: space-between;
  }

</style>