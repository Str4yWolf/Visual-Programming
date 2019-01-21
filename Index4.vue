<template>
  <q-page class="flex flex-center">
    <!-- function adapted from Vinodh's reference on Stine -->
    <button @click="addBlock('binarization')">add binarization</button>
    <binarization
      v-touch-pan="moveBlock" class="q-ma-md movable" :id="'binarizationBlock-'+(i-1)"
      :ref="'BinarizationBlock'+(i-1)"
      :style="{'left': binarizationBlocks[i-1][0] + 'px', 'top': binarizationBlocks[i-1][0] + 'px'}"
      v-for="i in binarizationBlocks.length" :key="'binarization'+i"></binarization>
    <rectangle-select class="select-comp"></rectangle-select>
    <edit-frame class="blocks_editor"></edit-frame>
  </q-page>
</template>

<style>
.blocks_editor {
  height: 800px;
  width: 50%;
  margin-right: 444px;
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
      initialPos: [100, 100], // this is the initial positions of a newly generated blocks [x, y]
      binarizationCounter: 0,
      binarizationBlocks: []
    }
  },
  methods: {
    // adds a block of the name given in the parameter
    addBlock: function (blockName) {
      if (blockName === 'binarization') {
        this.binarizationCounter += 1
        this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1]])
        alert('Binarization component #' + this.binarizationCounter + ' added')
        console.log('created ' + blockName + 'Block #' + this.binarizationCounter + ' at coordinates ' + this.initialPos)
      }
    },
    // deletes a block which called this function
    deleteBlock: function (blockName) {
      if (blockName === 'binarization') {
        this.binarizationCounter += 1
        this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1]])

        console.log('created ' + blockName + 'Block #' + this.binarizationCounter + ' at coordinates ' + this.initialPos)
      }
    },
    // find out which element is moving (adapted from Vinodh's reference on Stine)
    getActiveElement: function (event) {
      if (event.evt.target.className.includes('movable')) {
        return event.evt.target.id.split('-')
      } else {
        event.evt.path.forEach(function (element) {
          if (element.className.includes('movable')) {
            return element.id.split('-')
          }
        })
      }
    },
    // moves the block which triggered the event
    moveBlock: function (event) {
      // block who triggered event
      var element = this.getActiveElement(event)
      // its name
      var name = element[0]
      // its number
      var index = element[1]

      console.log(name + '#?' + ' with index ' + index + ' is moving')
      // position reference
      var posVar = name + 's'

      // update positions
      this.$set(this[posVar][index], 0, this[posVar][index][0] + event.delta.x)
      this.$set(this[posVar][index], 1, this[posVar][index][1] + event.delta.y)
    }
  }
}
</script>
