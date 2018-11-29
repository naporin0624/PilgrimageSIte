<template>
  <div class="MapView">
    <search-component></search-component>
    <div class="siimple-grid">
      <div class="siimple-grid-row">
        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <map-component></map-component>
        </div>

        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <blog-component></blog-component>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import blog from "./blog.vue";
import search from "./SeachBar.vue";
import map from "./GoogleMap";

export default {
  name: "MainSite",
  components: {
    "blog-component": blog,
    "search-component": search,
    "map-component": map
  }
};
</script>
