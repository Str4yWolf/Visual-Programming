<template>
  <q-page class="flex flex-center">
    <!-- function adapted from Vinodh's reference on Stine -->
    <button @click="addBlock('binarization')">add binarization</button>
    <binarization
      v-touch-pan="moveBlock" class="q-ma-md movable" :id="'binarizationBlocks-'+(i-1)"
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
      binarizationBlocks: [],
      blocks: [binarizationBlocks]
    }
  },
  methods: {
    // adds a block of the name given in the parameter
    // each block has its own intype and outtype,
    // specifying what data can be input
    // and what can be output
    addBlock: function (blockName) {
      if (blockName === 'binarization') {
        this.binarizationCounter += 1
        this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1],
          'image', 'image'])
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
        // path doesn't work with every browser
        var path = event.evt.path || (event.evt.composedPath && event.evt.composedPath())
        path.forEach(function (element) {
          if (element.className.includes('movable')) {
            return element.id.split('-')
          }
        })
      }
    },
    // moves the block which triggered by the event
    moveBlock: function (event) {
      // block which triggered event
      var element = this.getActiveElement(event)
      // its name
      var name = element[0]
      // its number
      var index = parseInt(element[1])
      console.log(name + '#?' + ' with index ' + index + ' is moving')
      // update positions
      var newX = this[name][index][0] + event.delta.x
      var newY = this[name][index][1] + event.delta.y
      // console.log(newX, newY)
      this.$set(this[name], index, [newX, newY])

      var bB1
      if (typeof this.$refs[name + index].$el === 'undefined') {
        bB1 = this.$refs[name + index][0].$el.getBoundingClientRect()
      } else {
        bB1 = this.$refs[name + index].$el.getBoundingClientRect()
      }

      for (b in this.blocks) {
        for (sb in b) {
          if (sb !== this[name][index]) {
            var bB2
            
            if (typeof sb === 'undefined') {
              bB2 = sb.getBoundingClientRect()
            } else {
              bB2 = sb.getBoundingClientRect()
            }

            // dock
            var overlap = !(bB1.right < bB2.left ||
                            bB1.left > bB2.right ||
                            bB1.bottom < bB2.top ||
                            bB1.top < bB2.bottom)
            
            if (!false) {
              console.log(name + index + 'collided with ' + sb)
              // if(element[2] == sb[3])
            }
          }
        }
      }
    }
  }
}
</script>
