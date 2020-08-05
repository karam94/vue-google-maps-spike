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
import GoogleMapLoader from "@/components/GoogleMapLoader";
import GoogleMapMarker from "@/components/GoogleMapMarker";

import { mapSettings } from "@/constants/mapSettings";

export default {
  components: {
    GoogleMapLoader,
    GoogleMapMarker
  },

  data() {
    return {
      markers: [
        {
          id: "AND Kilburn Office",
          position: { lat: -34.77194, lng: 138.61895 },
        },
        {
          id: "Co-op One Angel Square",
          position: { lat: 53.48769, lng: -2.23712 },
        },
        {
          id: "AND Murray Office",
          position: { lat: 53.7934982, lng: -1.5578858 },
        },
      ],
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
