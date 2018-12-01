<template>
  <div class="siimple-navbar siimple-navbar--teal">
    <div class="siimple-navbar-title">Home</div>
    <div class="siimple--float-right">
      <a class="siimple-navbar-item" href="#/">blog</a>
      <a class="siimple-navbar-item" href="#/hello">about</a>
      <input
        type="text"
        class="siimple-input siimple-input--light"
        placeholder="SEARCH"
        v-model="searchWord"
      >
      <div class="siimple-btn siimple-btn--grey" @click="searchButton">検索</div>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
import axios from "axios";
export default {
  name: "SearchBar",
  data() {
    return {
      searchWord: ""
    };
  },
  methods: {
    searchButton: function() {
      this.$emit("search", this.searchWord);
    }
  }
};
</script>
