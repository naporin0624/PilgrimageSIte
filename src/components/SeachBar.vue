<template>
  <div class="siimple-navbar siimple-navbar--teal">
    <div class="siimple-navbar-title">Home</div>
    <div class="siimple--float-right">
      <a class="siimple-navbar-item" href="#/">blog</a>
      <a class="siimple-navbar-item" href="#/hello">about</a>
      <input type="text" class="siimple-input siimple-input--light" placeholder="SEARCH" v-model="item">
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "SearchBar",
  data() {
    return {
      item: ""
    };
  }
};
</script>
