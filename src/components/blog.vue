<template>
  <div class="siimple-card">
    <div class="siimple-card-header siimple--text-center">{{blogData.title}}</div>

    <div class="scroll">
      <div
        class="siimple-card-body"
        v-bind:class="{'siimple--bg-light':activeItem === item}"
        v-for="item in blogData.locationData"
        v-bind:key="item.title"
        @mouseover="activeItem=item"
        @mouseout="activeItem=''"
        @click="clickCard(item)"
      >
        <div class="siimple-grid">
          <div class="siimple-grid-row">
            <div class="siimple-grid-col siimple-grid-col--4 siimple-grid-col--sm-hide">
              <img :src="item.image">
            </div>

            <div class="siimple-grid-col siimple-grid-col--8 siimple-grid-col--sm-12">
              <div class="siimple-h3">{{item.title}}</div>

              <p class="siimple-p">{{item.text}}</p>
              <p class="siimple-p">場所: {{item.location}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="siimple-card-footer siimple--text-right">{{blogData.author}}</div>
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
  height: 78vh;
  overflow-y: scroll;
}

img {
  width: 15vw;
}
</style>

