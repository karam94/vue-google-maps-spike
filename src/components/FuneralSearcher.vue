<template>
  <div class="funeral-search-container">
    <h1>Search for a funeral home near</h1>
    <input type="text" v-model="town" placeholder="Town or postcode" />
  </div>
</template>

<script>
export default {
  data() {
    return {
        town: ""
    };
  },
};
</script>

<style>
.funeral-search-container {
  position: absolute;
  z-index: 10;
  display: block;
  width: 420px;
  margin: 15px;
  padding: 15px;
  background-color: white;
  box-shadow: 0 0 3px 0 rgba(0, 0, 0, 0.4);
  text-align: left;
}
</style>
