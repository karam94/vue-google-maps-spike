<template>
  <div class="funeral-search-container">
    <h1>Search for a funeral home near</h1>
    <input type="text" v-model="town" placeholder="Town or postcode" />

    <div class="funeral-search-centers">
      <div class="card" v-for="center in funeralCenters" :key="center.id">
        {{ center.id }} <br/>
        {{ center.phone }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    funeralCenters: Array,
  },

  data() {
    return {
      town: "",
    };
  },
};
</script>

<style>
.funeral-search-container {
  position: absolute;
  z-index: 10;
  display: block;
  width: 320px;
  max-height: 814px;
  margin: 15px;
  padding: 15px;
  background-color: white;
  box-shadow: 0 0 3px 0 rgba(0, 0, 0, 0.4);
  text-align: left;
  overflow:hidden;
}

.funeral-search-centers {
  overflow: auto;
  height: 600px;
}

.card {
  width: 300px;
  height: 200px;
  margin-top: 20px;
  margin-bottom: 20px;
  box-shadow: 0 0 3px 0 rgba(0, 0, 0, 0.4);
  cursor: pointer;
}
</style>
