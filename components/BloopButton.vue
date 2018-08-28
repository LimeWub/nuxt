<template lang="pug">
    button {{ buttonText }}
      canvas.button__canvas(v-on:mousemove="mousemove" v-on:click="bloop" ref="canvas")
</template>


<script>
export default {
  data: () => {
    return {
      
    };
  },
  props: {
    buttonText: {
      type: String,
      required: true
    }
  },
  components: {
  },
  methods: {
    animate: (canvas) => {
      function redraw() {
        canvas.ctx.clearRect(0,0,canvas.width,canvas.height)
        if (canvas.pointer.draw) {
          
          if (canvas.pointer.rCurrent < canvas.pointer.rMin){
            canvas.pointer.rCurrent = canvas.pointer.rMin
          }
          // Is it Animating?
          // Should I add animating points? Yes.
          if (canvas.pointer.rCurrent > canvas.pointer.rMax){
            canvas.pointer.rCurrent = canvas.pointer.rMin
          } 
        }
        
        if (canvas.bloops.length) {
          for (let i = 0; i < canvas.bloops.length; i++ ){
            canvas.bloops[i].draw(canvas);
            canvas.bloops[i].r += 1;
          }

          canvas.bloops = canvas.bloops.filter(bloop => bloop.rMax >= bloop.r);
        }
        requestAnimationFrame(redraw);
      }
      requestAnimationFrame(redraw);
    },
    mousemove: (event) => {
      const canvas = event.target;
      let x = Math.floor(event.clientX - canvas.getBoundingClientRect().left);
      let y = Math.floor(event.clientY - canvas.getBoundingClientRect().top);

      canvas.pointer = {
        x: x,
        y: y
      };
      canvas.pointer.draw = true;
    },
    bloop: (event) => {
      const canvas = event.target;
      let x = Math.floor(event.clientX - canvas.getBoundingClientRect().left);
      let y = Math.floor(event.clientY - canvas.getBoundingClientRect().top);
      canvas.bloops.push({
        x: x,
        y: y,
        rMin: 1,
        rMax: 100,
        r: 1,
        color: 'white',
        draw: function(canvas) {
          canvas.ctx.save();
          canvas.ctx.globalAlpha = (this.rMax/this.r - 1)* 0.1;
          console.log(this.rMax/this.r);
          canvas.ctx.beginPath();
          canvas.ctx.arc(this.x, this.y, this.r, 0, 2 * Math.PI, true);
          canvas.ctx.fillStyle = this.color;
          canvas.ctx.fill();
          canvas.ctx.restore();
        }
      })
      
    }
  },
  mounted : function() {
      let canvas = this.$refs.canvas;
      canvas.width  = canvas.offsetWidth;
      canvas.height = canvas.offsetHeight;
      canvas.ctx = canvas.getContext('2d');
      canvas.pointer = {
        x: canvas.width/2,
        y: canvas.height/2,
        r: 10
      }
      canvas.bloops = [];
      this.animate(canvas);
  }
};


</script>

<style lang="scss">
.button__canvas{
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}
</style>