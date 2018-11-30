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
        v-model="item"
      >
      <div class="siimple-btn siimple-btn--grey" @click="Search">検索</div>
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
      item: "",
      base_url: ""
    };
  },
  methods: {
    Search: function() {
      axios.get(this.base_url, { params: { serach: this.item } }).then(res => {
        console.log(res);
        this.$emit("blog", res.data);
      });
    }
  }
};
</script>
