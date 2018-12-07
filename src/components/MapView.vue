<template>
  <div class="MapView">
    <search-component v-on:search="searchBlog" v-bind:blogData="blogData"></search-component>
    <div class="siimple-grid">
      <div class="siimple-grid-row">
        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <map-component v-bind:position="position" v-bind:locationData="blogData.locationData"></map-component>
        </div>

        <div class="siimple-grid-col siimple-grid-col--6 siimple-grid-col--sm-12">
          <blog-component v-on:position="setPosition" v-bind:blogData="blogData"></blog-component>
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

import axios from "axios";

// import loveliveBlogData from "../assets/json/lovelive.json";

export default {
  name: "MainSite",
  data() {
    return {
      blogData: null,
      position: { lat: 35.6693863, lng: 139.6012972 },
      info: null
    };
  },
  components: {
    "blog-component": blog,
    "search-component": search,
    "map-component": map
  },
  methods: {
    setPosition: function(position) {
      this.position = position;
    },
    searchBlog: function(searchWord) {
      alert(searchWord);
      axios.get(this.base_url, { params: { serach: this.item } }).then(res => {
        // console.log(res);
        this.$emit("search", res.data);
      });
    },
    setLoveLive: function() {
      var myJsonUrl = "http://" + location.host + "/static/json/lovelive.json";

      axios
        .get(myJsonUrl)
        .then(res => {
          console.log(res);
          this.blogData = res.data;
        })
        .fail(res => {
          console.log(res);
        });
    }
  },
  mounted: function() {
    this.setLoveLive();
  },
  watch: {}
};
</script>

<style>
html,
body {
  overflow: hidden;
}
</style>
