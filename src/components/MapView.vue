<template>
  <div class="MapView">
    <search-component v-on:blog="GetBlog" v-bind:blog="blog"></search-component>
    <div class="siimple-grid">
      <div class="siimple-grid-row">
        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <map-component v-bind:position="position"></map-component>
        </div>

        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <blog-component v-on:position="GetPosition"></blog-component>
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
  data() {
    return {
      position: { lat: 35.6693863, lng: 139.6012972 },
      blog: null
    };
  },
  components: {
    "blog-component": blog,
    "search-component": search,
    "map-component": map
  },
  methods: {
    GetPosition: function(position) {
      this.position = position;
    },
    GetBlog: function(blog) {
      this.blog = blog;
    }
  },
  watch: {
    blog() {
      console.log(this.blog);
    }
  }
};
</script>
