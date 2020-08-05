<template>
  <GoogleMapLoader :mapConfig="mapConfig" apiKey="">
    <template slot-scope="{ google, map }">
      <GoogleMapMarker
        v-for="marker in markers"
        :key="marker.id"
        :marker="marker"
        :google="google"
        :map="map"
      />
    </template>
  </GoogleMapLoader>
</template>

<script>
import GoogleMapLoader from "./GoogleMapLoader";
import GoogleMapMarker from "./GoogleMapMarker";

import { mapSettings } from "@/constants/mapSettings";

export default {
  components: {
    GoogleMapLoader,
    GoogleMapMarker,
  },

  data() {
    return {
      markers: [
        {
          id: "AND Kilburn Office",
          position: { lat: -34.771940, lng: 138.618950 },
        },
        {
          id: "Co-op One Angel Square",
          position: { lat: 53.487690, lng: -2.237120 },
        },
        {
          id: "AND Murray Office",
          position: { lat: 53.7934982, lng: -1.5578858 },
        }
      ]
    };
  },

  computed: {
    mapConfig() {
      return {
        ...mapSettings,
        center: this.mapCenter,
      };
    },

    mapCenter() {
      return this.markers[1].position;
    },
  },
};
</script>
