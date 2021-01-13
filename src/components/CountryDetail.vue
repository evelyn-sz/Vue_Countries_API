<template lang="html">
    <div v-if="country">
        <h3>{{ country.name }}</h3>
        <p>Capital: {{ country.capital }}</p>
        <p>Population: {{ country.population }}</p>
        <img id="lrg-flag" :src="country.flag" width="300px" />
    </div>
  
</template>

<script>

export default {
    name: 'country-detail',
    props: ['country']
}
</script>

<style lang="css" scoped>

</style>