<template>
  <div class="hello">
    <GmapMap
      :center="{lat:position.lat, lng:position.lng}"
      :zoom="15"
      map-type-id="terrain"
      style="width: 100%; height: 91.5vh"
    >
      <GmapMarker :position="{lat:position.lat, lng:position.lng}"/>
    </GmapMap>
    <!-- <GmapMarker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        :clickable="true"
        :draggable="true"
        @click="center=m.position"
      />
    </GmapMap>-->
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "Map",
  data() {
    return {};
  },
  props: ["position"]
};
</script>
