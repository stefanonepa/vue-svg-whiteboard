<template>
  <svg :width="size" :height="size" @click="draw($event)" @mousedown="startDrag" @mouseup="stopDrag" @mousemove="onDrag">
      <template v-for="element in elements">
        <vtriangle :x="element.x" :y="element.y" :size="element.size" :style="style"></vtriangle>
      </template>
  </svg>
</template>

<script>
  import vtriangle from './vtriangle';

  export default {
    data(){
      return {
        clickInfo: {
          dragging: false,
          startX: 0,
          startY: 0
        },
        size: 400,
        elements: [],
        style: {
          fill: 'royalblue'
        }
      }
    },
    methods:{
      startDrag (e) {
        this.clickInfo.dragging = true
        this.clickInfo.startX = e.pageX
        this.clickInfo.startY = e.pageY
      },
      onDrag (e){

      },
      stopDrag (e) {
        if (this.clickInfo.dragging) {
          this.clickInfo.dragging = false
          let a = Math.pow((this.clickInfo.startX - e.pageX), 2);
          let b = Math.pow((this.clickInfo.startY - e.pageY), 2);
          let size = Math.sqrt(a+b);
          console.log(size);
          this.elements.push({x: e.pageX, y: e.pageY, size});
        }
      },
      draw(evt){
        //this.elements.push({x: evt.x, y: evt.y})
        //console.log(evt)
      }
    },
    components:{
      vtriangle
    }
  }
</script>
<style>
  svg{
    border: 1px solid black;
  }
</style>