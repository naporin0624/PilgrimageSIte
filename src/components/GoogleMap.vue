<template>
  <div>
    <div>
      <h2>Search and add a pin</h2>
      <!-- <label>
        <gmap-autocompletez @place_changed="setPlace">
        </gmap-autocompletez>
        <button @click="addMarker">Add</button>
      </label> -->
      <br />

    </div>
    <br>
    <gmap-map></gmap-map>
  </div>
</template>

<script>
/* eslint-disable */
import {
  gmapMap,
  gmapMarker,
  gmapCluster,
  gmapInfoWindow,
  loaded
} from "vue2-google-maps";
export default {
  name: "GoogleMap",
  components: {
    "gmap-map": gmapMap
  },
  data() {
    return {
      // default to Montreal to keep it simple
      // change this to whatever makes sense
      center: {
        lat: 45.508,
        lng: -73.587
      },
      markers: [],
      places: [],
      currentPlace: null
    };
  },

  mounted() {
    this.geolocate();
  },

  methods: {
    // receives a place object via the autocomplete component
    setPlace(place) {
      this.currentPlace = place;
    },
    addMarker() {
      if (this.currentPlace) {
        const marker = {
          lat: this.currentPlace.geometry.location.lat(),
          lng: this.currentPlace.geometry.location.lng()
        };
        this.markers.push({
          position: marker
        });
        this.places.push(this.currentPlace);
        this.center = marker;
        this.currentPlace = null;
      }
    },
    geolocate: function() {
      navigator.geolocation.getCurrentPosition(position => {
        this.center = {
          lat: position.coords.latitude,
          lng: position.coords.longitude
        };
      });
    }
  }
};
</script>
