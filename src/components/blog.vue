<template>
  <div>
    <div class="title">
      <span>{{blogData.title}}</span>
    </div>
    <div class="scroll">
      <div
        class="article"
        v-for="item in blogData.locationData"
        v-bind:key="item.title"
        @click="clickCard(item)"
      >
        <div class="image-box">
          <img :src="item.image">
        </div>
        <div class="document-box">
          <div class="siimple-h4">{{item.title}}</div>
          <div class="siimple-p" id="text">{{item.text}}</div>
          <div class="siimple-p" id="location">場所: {{item.location}}</div>
        </div>
      </div>
    </div>
    <div class="author">
      <span>{{blogData.author}}</span>
    </div>
  </div>
</template>

<script>
/*eslint-disable*/
export default {
  name: "blog",
  data() {
    return {
      activeItem: ""
    };
  },
  methods: {
    clickCard: function(item) {
      this.$emit("position", item.position);
    }
  },
  mounted: function(){
    this.clickCard(this.blogData.locationData[0]);
  },
  props: ["blogData"]
};
</script>

<style>
.scroll {
  height: 84.7vh;
  overflow-y: scroll;
  /* border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8; */
}
.article:after {
  content: "";
  display: block;
  clear: both;
}
.article:hover {
  background-color: #f2f2f2;
}
.image-box {
  float: left;
  width: 40%;
  padding: 5px;
}
.document-box {
  float: none;
  width: auto;
  padding: 5px;
}
.image-box img {
  width: 100%;
}
.title {
  text-align: center;
  /* border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  border-top: medium solid #d8d8d8;
  border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8; */
}
.title span {
  font-size: 170%;
  font-weight: bold;
}
.author {
  text-align: right;
  /* border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px; */
  /* border-bottom: medium solid #d8d8d8;
  border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8; */
}
.author span {
  font-size: 120%;
  margin-right: 10px;
}
</style>

