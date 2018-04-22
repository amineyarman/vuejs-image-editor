<template>
  <div id="sliders-container">
    <div id="toggle-sliders" @click="slidersVisible = !slidersVisible">
      {{setButtonState}}
    </div>
    <div id="sliders-wrapper" v-show="slidersVisible">
    <RangeSlider
      v-model="sliderValues.grayscale"
      v-on:input="updateFilters"
      :min="0"
      :max="1"
      :step="0.01"
      :label="'grayscale'"
    ></RangeSlider>
    <RangeSlider
      v-model="sliderValues.blur"
      v-on:input="updateFilters"
      :min="0"
      :max="10"
      :step="0.5"
      :label="'blur'"
    ></RangeSlider>
    <RangeSlider
      v-model="sliderValues.brightness"
      v-on:input="updateFilters"
      :min="0"
      :max="5"
      :step="0.01"
      :label="'brightness'"
    ></RangeSlider>
    <RangeSlider
      v-model="sliderValues.contrast"
      v-on:input="updateFilters"
      :min="0"
      :max="5"
      :step="0.01"
      :label="'contrast'"
    ></RangeSlider>
    <RangeSlider
      v-model="sliderValues.saturate"
      v-on:input="updateFilters"
      :min="0"
      :max="5"
      :step="0.01"
      :label="'saturate'"
    ></RangeSlider>
  </div>    
  </div>
</template>

<script>
import RangeSlider from "./RangeSlider.vue";

export default {
  data() {
    return {
      sliderValues: {
        grayscale: 0,
        blur: 0,
        brightness: 1,
        contrast: 1,
        saturate: 1,
        unit: {
          blur: "px"
        }
      },
      slidersVisible: true
    }
  },
  computed: {
    setButtonState: function() {
      return this.slidersVisible ? "close":"edit"
    }
  },
  methods: {
    updateFilters() {
      this.$emit("slider-values", this.sliderValues);
    }
  },
  components: {
    RangeSlider
  }
};
</script>

<style lang="scss" scoped>
  #sliders-container {
    position: absolute;
    top: 0;
    right: 0;
    background-color: rgba(0,0,0,0.5);
    color: white;

    #sliders-wrapper {
      padding: 35px 10px 15px 10px;
    }

    #toggle-sliders {
      position: absolute;
      right: 0;
      background-color: #008CBA;
      padding: 3px 10px;
      cursor: pointer;
    }
  }
</style>
