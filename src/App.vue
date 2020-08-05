<template>
  <div>
    <TravelMap class="travel-map" />
  </div>
</template>

<script>
import TravelMap from "./components/TravelMap";

export default {
  name: "App",
  components: {
    TravelMap,
  },
};
</script>

<style scoped>
.travel-map {
  position: absolute;
  height: 100%;
  width: 100%;
}
</style>
