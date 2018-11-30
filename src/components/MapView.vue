<template>
  <div class="MapView">
    <search-component v-on:search="searchBlog" v-bind:blog="blog"></search-component>
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

export default {
  name: "MainSite",
  data() {
    return {
      blogData: {
        title: "ラブライブサンシャインの聖地",
        author: "hogehoge",
        locationData: [
          {
            title: "三津海水浴場",
            image: require("../assets/mitokaisui.jpg"),
            text:
              "三津海水浴場では様々なシーンで、アニメに使われています。たとえば、『ラブライブ!サンシャイン!!』の2話で島を眺めるシーンや背景にホテルが写っているシーンなどがあげられます。",
            location: "沼津市内浦三津",
            position: { lat: 35.0207124, lng: 138.8973772 }
          },
          {
            title: "安田屋旅館",
            image: require("../assets/yasudaya.jpg"),
            text:
              "安田屋旅館とは「高海千歌の実家が旅館」のモデルになった場所です。フィギュアやポスター、交流ノートなど多数あります。ファン交流会も行っているので、共通の仲間と知り合えるいい場所になります。一方で、安田屋旅館では、太宰治のゆかりのある場所です。小説「斜陽」の第1章・2章については安田屋旅館で生まれたと言われており、数奇家風の館内は有形文化財にも登録されています。",
            location: "静岡県沼津市内浦三津19",
            position: { lat: 35.020424, lng: 138.897573 }
          },
          {
            title: "伊豆・三津シーパラダイス",
            image: require("../assets/si-paradaisu.jpg"),
            text:
              "『ラブライブ!サンシャイン!!』に出てくる2ndシングル、「恋になりたいAQUARIUM」のPVのほとんどを伊豆・三津シーパラダイスを題材にしています。水族館の玄関や、メイン水族館の広場、イルカのモニュメントなどたくさんのものがあげられます。館内ではみとしーの記念撮影した後の、写真ホルダーを販売しており大人気です。また、みとしーでは40周年記念としてセイウチの特別イベントやお客様のアイデアを反映した特別企画を行っています",
            location: "静岡県沼津市内浦長浜3-1",
            position: { lat: 35.019483, lng: 138.895966 }
          },
          {
            title: "長井崎中学校周辺",
            image: require("../assets/nagaityuu.jpg"),
            text:
              "Aqoursの1stシングルの『君のこころは輝いてるかい？』のPVでメインに出てくる長井崎中学校。Aqoursの3人が歌う長井崎中学校体育館や長井崎中学校へ続く坂や長井崎中学校バス停前などがあります。長井崎中学校周辺の景色は、本編ではメインの場所になっています。",
            location: "静岡県沼津市内浦重須453",
            position: { lat: 35.0211574, lng: 138.8830119 }
          },
          {
            title: "松月",
            image: require("../assets/syogetu.jpg"),
            text:
              "CDになった「元気全開DAY!DAY!DAY!」のドラマパートの詩のタイトルにもなった松月。歌詞の内容が、みかんのお菓子についての内容のため、みかんのお菓子の売れ行きが向上しているそうです。",
            location: "静岡県沼津市内浦三津88−36",
            position: { lat: 35.022259, lng: 138.897925 }
          },
          {
            title: "あわしまマリンパーク",
            image: require("../assets/awashima.jpg"),
            text:
              "『Aqours』の松浦果南が働いているダイビングショップのモデルとなっている建物です。実際の館内は、世界の希少なカエルを多数みることができるカエル館です。アニメにでてくるボンベは再現されています。",
            location: "静岡県沼津市内浦重寺186",
            position: { lat: 35.0335475, lng: 138.8899908 }
          }
        ]
      },
      position: { lat: 35.6693863, lng: 139.6012972 },
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
    }
  },
  watch: {}
};
</script>
