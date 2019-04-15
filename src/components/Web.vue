<template>
  <section>
    <h2>CONTENU WEB</h2>
    <img src="../../public/zigzag.svg" alt>
    <div class="container-fluid">
      <div class="row">
        <div class="cache"></div>
        <div class="col-1">
          <button id="left-button" @click="swipeLeft">
            <strong><</strong>
          </button>
        </div>
        <div class="col-10">
          <div class="slide">
            <div class="container-fluid">
              <div class="center row" id="content" ref="content">
                <Card v-for="(item,index) in articles" :key="index" :article="item"></Card>
              </div>
            </div>
          </div>
        </div>

        <div class="col-1">
          <button id="right-button" @click="swipeRight">
            <strong>></strong>
          </button>
        </div>
        <div class="cache-d"></div>
      </div>
    </div>
  </section>
</template>

<script>
import json from "./../../press.json";
import Card from "../components/Card.vue";

const articles = json.press.filter(el => {
  return el.type === "Site web" || el.type === "Blog";
});

export default {
  methods: {
    /**
     * scrollTo - Horizontal Scrolling
     * @param {(HTMLElement ref)} element - Scroll Container
     * @param {number} scrollPixels - pixel to scroll
     * @param {number} duration -  Duration of scrolling animation in millisec
     */
    scrollTo(element, scrollPixels, duration) {
      const scrollPos = element.scrollLeft;
      // Condition to check if scrolling is required
      if (
        !(
          (scrollPos === 0 || scrollPixels > 0) &&
          (element.clientWidth + scrollPos === element.scrollWidth ||
            scrollPixels < 0)
        )
      ) {
        // Get the start timestamp
        const startTime =
          "now" in window.performance
            ? performance.now()
            : new Date().getTime();

        function scroll(timestamp) {
          //Calculate the timeelapsed
          const timeElapsed = timestamp - startTime;
          //Calculate progress
          const progress = Math.min(timeElapsed / duration, 1);
          //Set the scrolleft
          element.scrollLeft = scrollPos + scrollPixels * progress;
          //Check if elapsed time is less then duration then call the requestAnimation, otherwise exit
          if (timeElapsed < duration) {
            //Request for animation
            window.requestAnimationFrame(scroll);
          } else {
            return;
          }
        }
        //Call requestAnimationFrame on scroll function first time
        window.requestAnimationFrame(scroll);
      }
    },
    swipeLeft() {
      const content = this.$refs.content;
      this.scrollTo(content, -300, 800);
    },
    swipeRight() {
      const content = this.$refs.content;
      this.scrollTo(content, 300, 800);
    }
  },
  data() {
    return {
      articles: articles
    };
  },
  components: {
    Card
  }
};
</script>

<style>
.cache {
  width: 25vh;
  height: 100%;
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#ffffff+73,ffffff+100&1+73,0+100 */
  background: -moz-linear-gradient(
    left,
    rgba(255, 255, 255, 1) 73%,
    rgba(255, 255, 255, 0) 100%
  ); /* FF3.6-15 */
  background: -webkit-linear-gradient(
    left,
    rgba(255, 255, 255, 1) 73%,
    rgba(255, 255, 255, 0) 100%
  ); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(
    to right,
    rgba(255, 255, 255, 1) 73%,
    rgba(255, 255, 255, 0) 100%
  ); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#ffffff', endColorstr='#00ffffff',GradientType=1 ); /* IE6-9 */
  position: absolute;

  z-index: 50;
}

.cache-d {
  width: 25vh;
  height: 100%;
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#ffffff+0,ffffff+17&0+0,1+17 */
  background: -moz-linear-gradient(
    left,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 1) 17%
  ); /* FF3.6-15 */
  background: -webkit-linear-gradient(
    left,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 1) 17%
  ); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(
    to right,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 1) 17%
  ); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00ffffff', endColorstr='#ffffff',GradientType=1 ); /* IE6-9 */
  position: absolute;
  right: 0;

  z-index: 50;
}

.row {
  margin: 0;
}

#left-button {
  width: 50px;
  height: 50px;
  background-color: #f8ad41;
  border-radius: 50%;
  color: white;
  font-size: 2em;
  border: none;
  z-index: 1000;
}

#right-button {
  width: 50px;
  height: 50px;
  background-color: #f8ad41;
  border-radius: 50%;
  color: white;
  font-size: 2em;
  border: none;
  z-index: 1000;
}

.col-1 {
  display: flex;
  text-align: center;
  padding-right: 0px;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.left {
  float: left;
  width: 50px;
  height: 200px;
  border: 1px solid black;
}

.internal {
  display: inline-block;
}

.row {
  flex-wrap: nowrap;
}

.center {
  width: 100%;

  margin: 1px;
  overflow: hidden;
  white-space: nowrap;
}

.right {
  width: 50px;
  height: 200px;
  border: 1px solid black;
}
.slide {
  display: flex;
}
.container-fluid {
  padding: 0 0 0 0;
}
</style>
