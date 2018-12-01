<template>
  <div class="hello">
    <GmapMap
      :center="{lat:position.lat, lng:position.lng}"
      :zoom="15"
      map-type-id="terrain"
      style="width: 100%; height: 91.5vh"
    >
      <!-- <GmapMarker label="*" :position="{lat:position.lat, lng:position.lng}"/>
    </GmapMap> -->
    <GmapMarker
        v-for="(m, index) in locationData"
        :label="index.toString()"
        :key="index"
        :position="{lat:m.position.lat, lng:m.position.lng}"
        :clickable="true"
        :draggable="true"
        @click="center=m.position"
      />
    </GmapMap>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "Map",
  data() {
    return {};
  },
  props: ["position", "locationData"]
};
</script>
