<template>
  <div class="slider">
  
    <div class="slide"
      :class="{ active: slideActive === index }"
      v-for="(slide, index) in slides"
      :key="slide.id"
      :style="{ 'background-image': 'url(' + slide.url +')' }">
      <h2 class="slider-text">
         {{ slide.sliderText }}
      </h2>
    </div>

    <div class="controls">
      <span class="dot"
        v-for="(slide, index) in slides"
        :key="slide.id"
        @click="dotClick(index)"></span>
    </div>

    {{ message }}
  </div>
</template>

<script>
export default {
  name: "slider",
  data() {
    return {
        message: 'Hello',
        sliderAllCount: 0,
        slideActive: 0,
        slideCurrent: 0,
        interval: null,
        slides: [
        { id: 1,
          sliderText: 'Slide 1',
          url: '/1.jpg',
          color: 'violet'
        },
        { id: 2,
          sliderText: 'Slide 2',
          url: '/2.jpg',
          color: 'pink'
        },
        { id: 3,
          sliderText: 'Slide 2',
          url: '/3.jpg',
          color: 'pink'
        }
      ]
    }
  },
  methods: {
    activateSlide: function(index) {
      this.slideActive = index;
    },
    nextSlide: function () {
      this.slideActive = (this.slideActive + 1) % this.slides.length;
      this.activateSlide(this.slideActive);
    },
    dotClick: function (index) {
      clearInterval(this.interval);
      this.activateSlide(index);
      this.interval = setInterval(this.nextSlide, 3000);
    }
  },
  created () {
    this.interval = setInterval(this.nextSlide, 3000)
  }
};
</script>

<style scoped>
.slider {
  position: relative;
  /* background: url('../assets/pic1.png'); */
}
.slide.active {
  padding: 100px 20px;
}

.slider-text {
  display: none;
}

.active .slider-text {
  color: #fff;
  font-size: 30px;
}
.controls {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
}
.dot {
  display: block;
  width: 10px;
  height: 10px;
  background: #fff;
  border-radius: 100%;
  margin: 20px 0;
  cursor: pointer;
  position: relative;
  transition: all ease .3s;
}
.dot:after {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 25px;
  height: 25px;
}
.dot.active {
  background: red;
}
.title {
  color: #fff;
  padding: 100px 20px;
}
</style>