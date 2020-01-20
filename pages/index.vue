<template>
  <div class="container mx-auto">
    <div class="slider">
      <div class="prev" @click="prevSlideHandler">
        ←
      </div>
      <no-ssr>
        <slider ref="slider" :options="options" @slide="slide" @tap="onTap" @init="onInit">
          <slideritem>
            <a href="" class="slide-item bg-red-500">
              1
            </a>
          </slideritem>
          <slideritem>
            <a href="" class="slide-item bg-yellow-500">
              2
            </a>
          </slideritem>
          <slideritem>
            <a href="" class="slide-item bg-green-500">
              3
            </a>
          </slideritem>
        </slider>
      </no-ssr>
      <div class="next" @click="nextSlideHandler">
        →
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { slider, slideritem } from 'vue-concise-slider'

export default {
  components: {
    slider,
    slideritem
  },
  data() {
    return {
      options: {
        thresholdDistance: 30,
        thresholdTime: 30,
        speed: 300,
        loop: true,
        pagination: true,
        itemAnimation: true,
        grabCursor: true,
        slidesToScroll: 1,
        currentPage: 0,
        freeze: false
      }
    }
  },
  methods: {
    nextSlideHandler() {
      this.$refs.slider.$emit('slideNext')
    },
    prevSlideHandler() {
      this.$refs.slider.$emit('slidePre')
    },
    slide(a) {
      // console.log(a)
    },
    touch(a) {
      // console.log(a)
    }
  }
}
</script>

<style>
.slider {
  display: flex;
  align-items: center;
  height: 280px;
  margin: auto;
}

.slider .slide-item {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.next,
.prev {
  flex: none;
  line-height: 1;
  font-size: 15px;
  box-sizing: border-box;
  cursor: pointer;
  border-radius: 100%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #eee;
  margin: 0 10px;
}
</style>
