<template>
  <div class="card brew-list">
    <ul class="list-group list-group-flush">
      <li class="list-group-item" 
        v-for="brew in brews" 
        :key="brew.index">{{ brew.name }}, {{ brew.city}} {{brew.state}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BrewList",
  props: {
    brews: Array
  }
}
</script>

<style lang="scss" scoped>
  .brew-list {
    overflow-y: auto;
    height: 90vh;
    li {
      &:hover {
        background-color: darkgrey;
      }
    }
  }
</style>
