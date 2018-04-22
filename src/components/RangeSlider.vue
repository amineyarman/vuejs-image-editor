<template>
  <div>
    <label>
    <div>{{labelRange}}</div>
    <div>{{getValue}}</div>
    </label>
    <input 
      type="range"
      :min="minRange"
      :max="maxRange"
      :step="stepRange "
      :value="value"
      ref="rangeSlider"
      @input="updateValue"
      >
  </div>
</template>

<script>
export default {
  props: ["max", "min", "step", "label", "value"],
  data() {
    return {
      minRange: this.min,
      maxRange: this.max,
      stepRange: this.step,
      labelRange: this.label
    };
  },
  computed: {
    getValue: function( ) {
      return this.value;
    },
  },
  methods: {
    updateValue() {
      this.$emit('input', this.$refs.rangeSlider.value);
    },
  },
};
</script>

<style scoped>
label {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  text-align: left;
  margin-bottom: -10px;
  margin-top: 5px;
}

input[type=range] {
  -webkit-appearance: none;
  width: 100%;
  margin: 1.55px 0;
}
input[type=range]:focus {
  outline: none;
}
input[type=range]::-webkit-slider-runnable-track {
  width: 100%;
  height: 3px;
  cursor: pointer;
  background: rgba(48, 113, 169, 0.78);
  border-radius: 25px;
}
input[type=range]::-webkit-slider-thumb {
  box-shadow: 0.9px 0.9px 1px #000031, 0px 0px 0.9px #00004b;
  height: 6px;
  width: 6px;
  border-radius: 50px;
  background: #ffffff;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -1.5px;
}
input[type=range]:focus::-webkit-slider-runnable-track {
  background: rgba(106, 163, 213, 0.8);
}
input[type=range]::-moz-range-track {
  width: 100%;
  height: 3px;
  cursor: pointer;
  background: rgba(48, 113, 169, 0.8);
  border-radius: 25px;
}
input[type=range]::-moz-range-thumb {
  box-shadow: 0.9px 0.9px 1px #000031, 0px 0px 0.9px #00004b;
  height: 6px;
  width: 6px;
  border-radius: 50px;
  background: #ffffff;
  cursor: pointer;
}
input[type=range]::-ms-track {
  width: 100%;
  height: 3px;
  cursor: pointer;
}
input[type=range]::-ms-fill-lower {
  background: rgba(25, 60, 90, 0.78);
  border-radius: 50px;
}
input[type=range]::-ms-fill-upper {
  background: rgba(48, 113, 169, 0.8);
  border-radius: 50px;
}
input[type=range]::-ms-thumb {
  box-shadow: 0.9px 0.9px 1px #000031, 0px 0px 0.9px #00004b;
  border: 0px solid rgba(0, 0, 30, 0);
  height: 6px;
  width: 6px;
  border-radius: 50px;
  background: #ffffff;
  cursor: pointer;
  height: 3px;
}
input[type=range]:focus::-ms-fill-lower {
  background: rgba(48, 113, 169, 0.8);
}
input[type=range]:focus::-ms-fill-upper {
  background: rgba(106, 163, 213, 0.8);
}

</style>
