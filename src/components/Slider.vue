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
        :class="{ active: slideActive === index }"
        v-for="(slide, index) in slides"
        :key="slide.id"
        @click="dotClick(index)"></span>
    </div>

    <div class="slider__title">
      <h2>Comfort that<br>comes naturally</h2>
    </div>

    <div class="slider__links">
      <ul>
        <li><a href="#" class="slider__link">Shop men</a></li>
        <li><a href="#" class="slider__link">shop women</a></li>
      </ul>
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
      this.interval = setInterval(this.nextSlide, 10000);
    }
  },
  created () {
    this.interval = setInterval(this.nextSlide, 10000)
  }
};
</script>

<style scoped>
.slider {
  position: relative;
  /* background: url('../assets/pic1.png'); */
}
.slide {
  background-size: cover;
  background-position: center top;
  opacity: 0.5;
  transition: opacity ease 2s;
}
.slide.active {
  opacity: 1;
  padding: 45vh 45vw;
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
  background: transparent;
  border: 2px solid rgb(255, 255, 255);
  border-radius: 100%;
  margin: 10px 0;
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
  background: rgba(255, 255, 255, 0.9);
}
.title {
  color: #fff;
  padding: 100px 20px;
}
.slider__title {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  transform: translate(-50%, -50%) skew(0, -4deg);
  font-size: 50px;
  color: rgb(255, 255, 255);
  text-transform: uppercase;
  font-style: italic;
  letter-spacing: 8px;
  line-height: 1.5;
}
.slider__links {
  position: absolute;
  bottom: 70px;
  width: 100%;
  font-size: 16px;
  color: rgb(255, 255, 255);
  text-transform: uppercase;
  letter-spacing: 2px;
}
.slider__link {
  margin: 75px;
  padding-bottom: 15px;
  position: relative;
}
.slider__link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: calc(50% - 230px / 2);
  width: 230px;
  height: 2px;
  background-color: rgb(255, 255, 255);
  transition: all ease 0.3s;
}
.slider__link:hover::after {
  width: 100%;
  left: 0;
}

@media screen and (max-width: 768px) {
  .slider__title {
    font-size: 35px;
  }
}
</style>