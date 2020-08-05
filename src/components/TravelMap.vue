<template>
  <GoogleMapLoader :mapConfig="mapConfig" apiKey="" :funeralCenters="markers">
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
    GoogleMapMarker,
  },

  data() {
    return {
      markers: [
        {
          id: "AND Kilburn Office",
          phone: "123 456 789",
          position: { lat: 53.477459, lng: -2.242979 },
        },
        {
          id: "Co-op One Angel Square",
          phone: "123 456 456",
          position: { lat: 53.48769, lng: -2.23712 },
        },
        {
          id: "AND Murray Office",
          phone: "123 456 123",
          position: { lat: 53.7934982, lng: -1.5578858 },
        },
        {
          id: "My local Co-op",
          phone: "123 123 123",
          position: { lat: 53.72672, lng: -2.5151 },
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
