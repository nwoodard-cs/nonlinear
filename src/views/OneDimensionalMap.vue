<template>
  <div class="OneDimensionalMap">
      <h1>1D Map</h1>
      <div ref = "canvas" class = "d-flex justify-content-center"></div>
  </div>
</template>

<script>
import P5 from 'p5'

export default {
  name: 'OneDimensionalMap',
  data() {
    return {
      script: null,
      ps: null,
      x: 0,
      y: 0,
    }
  },
  mounted() {
    this.script = (p) => {
      this.x = 100
      this.y = 100
      p.setup = () => {
        this.canvas = p.createCanvas(600, 420)
        this.canvas.parent(this.$refs.canvas)
        p.frameRate(60)
      }
      p.draw = () => {
        p.background(0)
        p.fill(255)
        p.rect(this.x, this.y, 50, 50)
      }
    }
    this.ps = new P5(this.script)
  },
}
</script>
