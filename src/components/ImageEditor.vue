<template>
  <div>
    <div>

      <label for="loadImage">Load your picture</label>
      <input id="loadImage" type="file" placeholder="" @change="loadImage($event)" />
      
      <div id="saveImage" @click="download">Save</div>
      
      <div class="container">
        <div id="editor-container">
          <img 
            id="image"
            ref="img" 
            crossorigin="anonymous"
            :style="filters"
          >
          <SlidersBox @slider-values="updatedFilters($event)"></SlidersBox>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SlidersBox from "./SlidersBox.vue";

export default {
  data() {
    return {
      filterValues: {},
      unit: {
        blur: "px"
      }
    };
  },
  mounted() {
    this.$refs.img.src =
      "";
  },
  computed: {
    filters() {
      return {
        filter: Object.entries(this._data.filterValues)
          .filter(item => item[0] !== "unit")
          .map(item => `${item[0]}(${item[1]}${this.unit[item[0]] || ""})`)
          .join(" ")
      };
    }
  },
  methods: {
    updatedFilters(updatedfilters) {
      this.filterValues = updatedfilters;
    },
    loadImage(event){
      var image = event.target.files[0];
      var imageRead = new FileReader();
      
      imageRead.onload = function(loadEvent) {
        console.dir(loadEvent);
        document.querySelector('#image').setAttribute('src', loadEvent.target.result);
      };
      imageRead.readAsDataURL(image);
    },

    download() {
      const canvas = document.createElement('canvas')
      canvas.width = document.querySelector('img').clientWidth;
      canvas.height = document.querySelector('img').clientHeight;
      const ctx = canvas.getContext('2d')
      ctx.filter = this.filters.filter
      ctx.drawImage(this.$refs.img, 0, 0, canvas.width, canvas.height)
      const link = document.createElement('a')
      link.href = canvas.toDataURL()
      link.download = 'result.png'
      link.click()
    }
  },
  components: {
    SlidersBox
  }
};
</script>

<style lang="scss" scoped>
#editor-container {
  position: relative;
  width: 100%;
  margin-top: 10px;

  img {
    width: 100%;
    height: auto;
  }
}

input[type="file"] {
  display: none;
}

label, #saveImage {
  color:white;
  background-color: #008CBA;
  display: inline-block;
  padding: 6px 12px;
  cursor: pointer;
}

label {
  margin-right: 20px;
}

#saveImage {
  background-color: #8bc34a;
}
</style>
