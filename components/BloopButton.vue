<template lang="pug">

    a.btn(v-if="href" v-bind:href="href") {{ buttonText }}
      canvas.btn__canvas(v-on:click="bloop" ref="canvas")

    button.btn(v-else) {{ buttonText }}
      canvas.btn__canvas(v-on:click="bloop" ref="canvas")

</template>


<script>
export default {
  data: () => {
    return {
    };
  },
  computed: {},
  props: {
    href: {
      type: String,
      required: false
    },
    buttonText: {
      type: String,
      required: true
    }
  },
  components: {},
  methods: {
    animate: function(canvas) {
      let redraw = () => {
        canvas.ctx.clearRect(0, 0, canvas.width, canvas.height);
        if (canvas.bloops.length) {
          for (let i = 0; i < canvas.bloops.length; i++) {
            canvas.bloops[i].draw(canvas);
            canvas.bloops[i].r += 5;
          }
          canvas.bloops = canvas.bloops.filter(bloop => bloop.rMax >= bloop.r);
        }
        requestAnimationFrame(redraw);
      };
      requestAnimationFrame(redraw);
    },
    bloop: function(event) {
      const canvas = event.target;
      let x = Math.floor(event.clientX - canvas.getBoundingClientRect().left);
      let y = Math.floor(event.clientY - canvas.getBoundingClientRect().top);
      canvas.bloops.push({
        x: x,
        y: y,
        rMin: 1,
        rMax: 100,
        r: 1,
        color: window.getComputedStyle(this.$el).getPropertyValue("color"), // Should this be moved to a mouseover event?
        draw: function(canvas) {
          canvas.ctx.save();
          canvas.ctx.globalAlpha = (this.rMax / this.r - 1) * 0.1;
          canvas.ctx.beginPath();
          canvas.ctx.arc(this.x, this.y, this.r, 0, 2 * Math.PI, true);
          canvas.ctx.fillStyle = this.color;
          canvas.ctx.fill();
          canvas.ctx.restore();
        }
      });
    }
  },
  mounted: function() {
    let canvas = this.$refs.canvas;
    canvas.width = canvas.offsetWidth;
    canvas.height = canvas.offsetHeight;
    canvas.ctx = canvas.getContext("2d");
    canvas.bloops = [];
    this.animate(canvas);
  }
};
</script>

<style lang="scss">
.btn__canvas {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}
</style>