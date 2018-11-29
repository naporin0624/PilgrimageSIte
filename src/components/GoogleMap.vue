<template>
  <div class="hello">
    <GmapMap
      :center="{lat:position.lat, lng:position.lng}"
      :zoom="15"
      map-type-id="terrain"
      style="width: 49vw; height: 89vh"
    >
      <GmapMarker label="*" :position="{lat:position.lat, lng:position.lng}"/>
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
  name: "HelloWorld",
  data() {
    return {};
  },
  props: ["position"]
};
</script>
