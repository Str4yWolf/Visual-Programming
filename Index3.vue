<template>
  <q-page class="flex flex-center">
    <!-- function adapted from Vinodh's reference on Stine -->
    <binarization
      :style="{'left':x1 + 'px', 'top': y1 + 'px'}"
      class="q-ma-md movable"
      @mousedown.native="moveStart($event,1)"
      @mouseup.native="moveEnd($event,1)"
      @mousemove.native="moveActive($event,1)"></binarization>
    <editFrame class="blocks_editor"></editFrame>
  </q-page>
</template>

<style>

.blocks_editor {
  height: 800px;
  width: 50%;
  margin-right: 444px;
  border-style: solid;
  border-radius: 10px;
  border-color: blue;
}

.movable {
  display: inline-block;
  padding: 0px;
  position: absolute;
}
</style>

<script>
import Binarization from '../components/Binarization.vue'
import editFrame from '../components/editFrame.vue'
export default {
  name: 'PageIndex',
  components: {
    Binarization,
    editFrame
  },
  data () {
    return {
      x1: 100,
      y1: 100
    }
  },
  methods: {
    moveStart: function (event, index) {
      console.log('start')
      this.moving = true
      this['offsetInitX' + index] = event.offsetX
      this['offsetInitY' + index] = event.offsetY
    },
    moveActive: function (event, index) {
      if (this.moving) {
        console.log('move')
        this['x' + index] += event.offsetX - this['offsetInitX' + index]
        this['y' + index] += event.offsetY - this['offsetInitY' + index]
      }
    },
    moveEnd: function (event, index) {
      console.log('end')
      this.moving = false
    }
  }
}
</script>
