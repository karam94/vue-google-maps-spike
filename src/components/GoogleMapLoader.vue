<template>
  <div>
    <FuneralSearcher :funeralCenters="funeralCenters" />
    <div class="google-map" ref="googleMap"></div>

    <!-- If we have map markers/slot children components -->
    <template v-if="Boolean(this.google) && Boolean(this.map)">
      <slot :google="google" :map="map" />
    </template>
  </div>
</template>

<script>
import GoogleMapsApiLoader from "google-maps-api-loader";
import FuneralSearcher from "@/components/FuneralSearcher";

export default {
  props: {
    mapConfig: Object,
    apiKey: String,
    funeralCenters: Array
  },

  data() {
    return {
      google: null,
      map: null,
    };
  },

  components: {
    FuneralSearcher,
  },

  async mounted() {
    const googleMapApi = await GoogleMapsApiLoader({
      apiKey: this.apiKey,
    });
    this.google = googleMapApi;
    this.initializeMap();
  },

  methods: {
    initializeMap() {
      const mapContainer = this.$refs.googleMap;
      this.map = new this.google.maps.Map(mapContainer, this.mapConfig);
    },
  },
};
</script>

<style scoped>
.google-map {
  width: 100%;
  min-height: 100%;
}
</style>
