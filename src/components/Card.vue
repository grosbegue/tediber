<template>
  <div class="col-12 col-xl-4 col-lg-4 col-md-6 col-sm-6">
    <div class="cardi internal">
      <div class="bandeau">
        <div class="date">
          <p>{{article.date}}</p>
        </div>

        <div class="ribbon-wrapper">
          <div class="ribbon-front">
            <!-- ribbon text goe here -->
            <div class="type">{{article.type.toUpperCase()}}</div>
          </div>
          <div class="ribbon-edge-bottomright"></div>
        </div>
      </div>
      <div class="logo" :style="{'background-image':'url('+backgroundUrl+')'}"></div>
      <div class="contenu">
        <h5 class="magazine">{{article.name.toUpperCase()}}</h5>

        <h5 class="accroche">
          <strong>{{article.title}}</strong>
        </h5>
        <p class="texte">{{article.body}}</p>
      </div>
      <div class="btnLire" v-on:click="link(article)">
        <strong>LIRE LA SUITE</strong>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    article: {
      type: Object,
      required: true
    }
  },

  data: function() {
    return {
      backgroundUrl: this.article.logo
      // backgroundUrl: require("`" + this.article.logo + "`")
    };
  },
  mounted() {
    console.log("BGU", this.backgroundUrl);
    // console.log(this.article.logo);
    this.backgroundUrl = require(this.article.logo);
    // this.backgroundUrl = this.article.logo;
    console.log("swicth", this.backgroundUrl);
  },
  methods: {
    link: function(article) {
      window.open(article.url);
    }
  }
};
</script>



<style scoped>
.contenu {
  padding: 0px 10px 0px 10px;
}

.logo {
  height: 30px;
  width: 100%;

  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}

.accroche {
  display: flex;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
  min-height: 2.4em;

  justify-content: center;
  align-items: center;
}

.texte {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
  min-height: 76px;
}

.magazine {
  min-height: 2.4em;
  display: flex;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
  justify-content: center;
  align-items: center;
}

.bandeau {
  display: flex;
  justify-content: space-between;
  align-items: center;

  margin-top: 5px;
  margin-bottom: 13px;
}

.type {
  padding-top: 5px;
  color: white;
}

.date {
  padding-top: 15px;
  padding-left: 15px;
  font-size: 16px;
  color: #1e2345;
}

.btnLire {
  background-color: #f8ad41;
  padding: 5px 10px 5px 10px;
  color: white;
  display: inline;
  cursor: pointer;
}

.cardi {
  width: 100%;
  background-color: white;
  box-shadow: 0px 0px 10px lightgrey;
  padding-bottom: 20px;
  white-space: normal;
  margin-top: 20px;
  margin-bottom: 20px;
}
/* ribbon style */

.ribbon-wrapper {
  position: relative;
  width: 130px;
  margin-right: -20px;
}
.ribbon-wrapper .p {
  margin: 0px;
}

.ribbon-front {
  background-color: #1e2345;
  height: 40px;
  width: 100%;
  position: relative;
  left: 0px;
  z-index: 2;
  color: white;
  font-size: 21px;
  padding-top: 2px;
}

.ribbon-edge-topleft,
.ribbon-edge-topright,
.ribbon-edge-bottomleft,
.ribbon-edge-bottomright {
  position: absolute;
  z-index: 1;
  border-style: solid;
  height: 0px;
  width: 0px;
}

.ribbon-edge-bottomleft,
.ribbon-edge-bottomright {
  top: 42px;
}

.ribbon-edge-topleft,
.ribbon-edge-bottomleft {
  left: 0px;
  border-color: transparent #1e2345 transparent transparent;
}

.ribbon-edge-topleft {
  top: 0px;
  border-width: 0px 0px 0 0;
}
.ribbon-edge-bottomleft {
  border-width: 0 0px 0px 0;
}

.ribbon-edge-topright,
.ribbon-edge-bottomright {
  left: 80px;
  left: 110px;
  top: 40px;
  border-color: transparent transparent transparent #1e2345;
}

.ribbon-edge-topright {
  top: 0px;
  border-width: 0px 0 0 20px;
}
.ribbon-edge-bottomright {
  border-width: 0 0 15px 20px;
}

.ribbon-back-left {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 0px;
  height: 40px;
  z-index: 0;
}

.ribbon-back-right {
  position: absolute;
  top: 15px;
  right: 0px;
  width: 0px;
  height: 40px;
  z-index: 0;
}
</style>

