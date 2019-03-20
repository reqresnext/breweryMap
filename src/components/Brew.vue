<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Breweries List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <BrewList :brews="brews" />
      </div>
      <div class="col-6">
        <BrewMap :brews="brews" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import BrewList from './BrewList.vue';
import BrewMap from './BrewMap.vue';

export default {
  name: 'Brew',
  data: function() {
    return {
      brews: []
    }
  },
  mounted: function() {
    axios.get('https://api.openbrewerydb.org/breweries?by_state=california')
      .then(res => {
        this.brews = res.data;
      })
  },
  components: {
    BrewList,
    BrewMap
  }
}
</script>

<style lang="scss" scoped>

</style>

