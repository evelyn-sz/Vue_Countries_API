<template lang="html">
    <div>
        <li v-on:click="handleClick"> {{ country.name }} </li>
    </div>
  
</template>

<script>

import { eventBus } from '../main.js';
import CountryDetail from '../components/CountryDetail';

export default {
    name: 'list-item',
    props: ['country'],
    methods: {
        handleClick: function(){
            // console.log('country', this.country)
            eventBus.$emit('country-selected', this.country);
        }
        
    }

}
</script>

<style lang="css" scoped>

</style>