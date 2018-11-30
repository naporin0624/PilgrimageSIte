<template>
  <div>
    <div class="title">
      <span>{{title}}</span>
    </div>
    <div class="scroll">
      <div
        class="article"
        v-for="item in blogData"
        v-bind:key="item.title"
        @click="ClickCard(item)"
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
      <span>{{author}}</span>
    </div>
  </div>
</template>

<script>
/*eslint-disable*/
export default {
  name: "blog",
  data() {
    return {
      activeItem: "",
      title: "ラブライブサンシャインの聖地",
      author: "hogehoge",
      blogData: [
        {
          title: "三津海水浴場",
          image: require("../assets/mitokaisui.jpg"),
          text:
            "三津海水浴場では様々なシーンで、アニメに使われています。たとえば、『ラブライブ!サンシャイン!!』の2話で島を眺めるシーンや背景にホテルが写っているシーンなどがあげられます。",
          location: "沼津市内浦三津",
          position: {
            lat: 35.0207168,
            lng: 138.8951885
          }
        },
        {
          title: "安田屋旅館",
          image: require("../assets/yasudaya.jpg"),
          text:
            "安田屋旅館とは「高海千歌の実家が旅館」のモデルになった場所です。フィギュアやポスター、交流ノートなど多数あります。ファン交流会も行っているので、共通の仲間と知り合えるいい場所になります。一方で、安田屋旅館では、太宰治のゆかりのある場所です。小説「斜陽」の第1章・2章については安田屋旅館で生まれたと言われており、数奇家風の館内は有形文化財にも登録されています。",
          location: "静岡県沼津市内浦三津19",
          position: {
            lat: 35.0204284,
            lng: 138.8953843
          }
        },
        {
          title: "伊豆・三津シーパラダイス",
          image: require("../assets/si-paradaisu.jpg"),
          text:
            "『ラブライブ!サンシャイン!!』に出てくる2ndシングル、「恋になりたいAQUARIUM」のPVのほとんどを伊豆・三津シーパラダイスを題材にしています。水族館の玄関や、メイン水族館の広場、イルカのモニュメントなどたくさんのものがあげられます。館内ではみとしーの記念撮影した後の、写真ホルダーを販売しており大人気です。また、みとしーでは40周年記念としてセイウチの特別イベントやお客様のアイデアを反映した特別企画を行っています",
          location: "静岡県沼津市内浦長浜3-1",
          position: {
            lat: 35.0194874,
            lng: 138.8937773
          }
        },
        {
          title: "長井崎中学校周辺",
          image: require("../assets/nagaityuu.jpg"),
          text:
            "Aqoursの1stシングルの『君のこころは輝いてるかい？』のPVでメインに出てくる長井崎中学校。Aqoursの3人が歌う長井崎中学校体育館や長井崎中学校へ続く坂や長井崎中学校バス停前などがあります。長井崎中学校周辺の景色は、本編ではメインの場所になっています。",
          location: "静岡県沼津市内浦重須453",
          position: {
            lat: 35.0228559,
            lng: 138.8830116
          }
        },
        {
          title: "松月",
          image: require("../assets/syogetu.jpg"),
          text:
            "CDになった「元気全開DAY!DAY!DAY!」のドラマパートの詩のタイトルにもなった松月。歌詞の内容が、みかんのお菓子についての内容のため、みかんのお菓子の売れ行きが向上しているそうです。",
          location: "静岡県沼津市内浦三津88−36",
          position: {
            lat: 35.0605017,
            lng: 138.9484541
          }
        },
        {
          title: "あわしまマリンパーク",
          image: require("../assets/awashima.jpg"),
          text:
            "『Aqours』の松浦果南が働いているダイビングショップのモデルとなっている建物です。実際の館内は、世界の希少なカエルを多数みることができるカエル館です。アニメにでてくるボンベは再現されています。",
          location: "静岡県沼津市内浦重寺186",
          position: {
            lat: 35.0335519,
            lng: 138.8878021
          }
        }
      ]
    };
  },
  methods: {
    ClickCard: function(item) {
      this.$emit("position", item.position);
    }
  },
  props: ["blog"],
  watch: {
    blog() {
      console.log("blog-catch");
      console.log(this.blog);
    }
  }
};
</script>

<style>
.scroll {
  height: 84.7vh;
  overflow-y: scroll;
  border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8;
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
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  border-top: medium solid #d8d8d8;
  border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8;
}
.title span {
  font-size: 170%;
  font-weight: bold;
}
.author {
  text-align: right;
  border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px;
  border-bottom: medium solid #d8d8d8;
  border-left: medium solid #d8d8d8;
  border-right: medium solid #d8d8d8;
}
.author span {
  font-size: 120%;
  margin-right: 10px;
}
</style>
