<template>
  <div class="OneDimensionalMap">
      <h1>1D Map</h1>
      <h1>{{seed}}</h1>
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
      x: 0,
      y: 0,
      seed: 300,
    }
  },
  mounted() {
    // This p5 configuration is called "instance mode"
    this.script = (p) => {
      this.x = 100
      this.y = 100
      p.setup = () => {
        this.canvas = p.createCanvas(600, 420)
        this.canvas.parent(this.$refs.canvas)
        p.frameRate(1)
      }
      p.draw = () => {
        const r = p.random(255)
        const g = p.random(255)
        const b = p.random(255)

        if (this.seed % 2 === 0) this.seed /= 2
        else this.seed = 3 * this.seed + 1
        for (let i = 0; i < this.seed; ++i) {
          p.fill(r, g, b, 200)
          p.rect(p.random(550), p.random(370), 50, 50)
        }
      }
    }
    this.ps = new P5(this.script)
  },
}
</script>
