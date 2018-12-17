<template>
  <q-page class="flex flex-center">
    <!-- function adapted from Vinodh's reference on Stine -->
    <binarization
      :style="{'left': x1 + 'px', 'top': y1 + 'px'}"
      class="q-ma-md movable"
      @mousedown.native="moveStart($event,1)"
      @mouseup.native="moveEnd($event,1)"
      @mousemove.native="moveActive($event,1)"></binarization>
    <rectangle-select class="select-comp"></rectangle-select>
    <edit-frame class="blocks_editor"></edit-frame>
  </q-page>
</template>

<style>
.blocks_editor {
  height: 800px;
  width: 50%;
  margin-right: 44%;
  border-style: solid;
  border-radius: 10px;
  border-width: 8px;
  border-color: blue;
}
.movable {
  display: inline-block;
  padding: 0px;
  position: absolute;
}
.select-comp {
  position: fixed;
  top: 0px;
  right: 0px;
}
</style>

<script>
import Binarization from '../components/Binarization.vue'
import RectangleSelect from '../components/RectangleSelect.vue'
import EditFrame from '../components/editFrame.vue'
export default {
  name: 'PageIndex',
  components: {
    Binarization,
    RectangleSelect,
    EditFrame
  },
  data () {
    return {
      x1: 100,
      y1: 100,
      binarizationCounter: 0,
      binarizationBlocks: []
    }
  },
  methods: {
    moveStart: function (event, index) {
      console.log('index moveStart')
      this.moving = true
      this['offsetInitX' + index] = event.offsetX
      this['offsetInitY' + index] = event.offsetY
    },
    moveActive: function (event, index) {
      if (this.moving) {
        console.log('index moveActive')
        this['x' + index] += event.offsetX - this['offsetInitX' + index]
        this['y' + index] += event.offsetY - this['offsetInitY' + index]
      }
    },
    moveEnd: function (event, index) {
      console.log('index moveEnd')
      this.moving = false
    }
    /* addBlock: function (blocktype, index) {
      if (blocktype === 'binarization') {
        this.binarizationCounter += 1
        this.binarizationBlocks.push((
              'id': index,
              'x': 100,
              'y': 100))
      }
    } */
  }
}
</script>
