<template>
  <div id="info">
    <p>{{ width }}x{{ height }}px</p>
    <h1>{{ row_length }}</h1>
  </div>
  <div id="outer">

    <div id="container" ref="container" class="shadow-lg bg-body-tertiary rounded">
      <Rows v-for="row in Number(rows)" :key="row" :row_length="row_length" @getImageSize="getImageSize" class="rows" />
    </div>
  </div>
</template>

<script>
import Rows from "./components/Rows"
export default {
  name: 'App',
  data() {
    return {
      height: '',
      width: '',
      row_length: 1,
      rows: 1,
    }
  },
  components: {
    Rows
  },
  methods: {
    getImageSize() {
      // const img = new Image();
      // img.src = this.$refs.image.src;
      const img = document.getElementById('img')
      this.width = img.width
      this.height = img.height
      let screenWidth = this.$refs.container.clientWidth
      let screenHeight = this.$refs.container.clientHeight
      this.rows = Math.floor(screenHeight / this.height)
      this.row_length = Math.floor(screenWidth / this.width)
      console.log(this.rows)


    },
  },
  mounted() {
    window.addEventListener("resize", this.getImageSize);
  }
}  
</script>

<style>
#container {
  position: absolute;
  margin: auto;
  height: 100%;
  top: 0;
  bottom: 0
}

#outer {
  padding-left: 20%;
  height: 50%;
  margin: 10%;
}
</style>
