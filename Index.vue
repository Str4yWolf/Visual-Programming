<!-- TODO:
  clickButton from layout   90%: misses the final bus
  delete block              80%: misses the final deletion
  docking
  undocking
  selection frame
  emulate results
  -->
<template>
  <q-page class="flex flex-center">
    <!-- add a binarization block -->
    <button @click="addBlock('binarization')">add binarization
    </button>
    <binarization
      @emitted="receiveData"
      v-touch-pan="moveBlock" class="movable q-py-xl"
      :id="'binarizationBlock-'+(i-1)"
      :ref="'binarizationBlock-'+(i-1)"
      :style="{'left': binarizationBlocks[i-1][0] + 'px',
               'top': binarizationBlocks[i-1][1] + 'px'}"
      v-for="i in binarizationBlocks.length"
      :key="'binarizationBlock'+i">
    </binarization>
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
  z-index: -1;
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
  z-index: -1;
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
      // this is the initial positions of
      // a newly generated blocks [x, y]
      initialPos: [100, 100],
      binarizationCounter: 0,
      binarizationBlocks: [],
      blocks: [this.binarizationBlocks]
    }
  },
  updated () {
    this.$root.$on('addBlock', this.addBlock)
  },
  methods: {
    /*
            receives the data and passes it on
            to the action specified in the message
    */
    receiveData: function (data) {
      console.log('received data')
      if (data[0] === 'deleteBlock') {
        this.deleteBlock(data[1])
      }
    },
    /*
            adds a block of the name given in the parameter
            each block has its own intype and outtype,
            specifying what data can be input
            and what can be output
    */
    addBlock: function (blockName) {
      console.log('called addBlock with argument ' + blockName)
      if (blockName === 'binarization') {
        this.binarizationCounter += 1
        this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1],
          'image', 'image'])
        alert('Binarization component #' + this.binarizationCounter + ' added')
        console.log('created ' + blockName + 'Block #' + this.binarizationCounter + ' at coordinates ' + this.initialPos)
      }
    },
    /*
            deletes a block which called this function
    */
    deleteBlock: function (data) {
      console.log('called deleteBlock from Index')
      data = null
    },
    /*
            find out which element is moving
            (adapted from Vinodh's reference on Stine)
    */
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
    /*
            moves the block which triggered by the event
    */
    moveBlock: function (event) {
      // block which triggered event
      var element = this.getActiveElement(event)
      // console.log(event, element)
      // its name
      var blockArray = element[0] + 's'
      // its number
      var index = parseInt(element[1])
      console.log(name + '#?' + ' with index ' + index + ' is moving')
      // update positions
      var newX = this[blockArray][index][0] + event.delta.x
      var newY = this[blockArray][index][1] + event.delta.y
      console.log(newX, newY)
      this.$set(this[blockArray], index, [newX, newY])
      /* var bB1
      var ref = element[0] + '-' + index
      if (typeof this.$refs[ref].$el === 'undefined') {
        bB1 = this.$refs[ref][0].$el.getBoundingClientRect()
      } else {
        bB1 = this.$refs[ref].$el.getBoundingClientRect()
      }
      for (var b in this.blocks) {
        for (var sb in b) {
          if (sb !== this[blockArray][index]) {
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
            if (overlap) {
              console.log(name + index + 'collided with ' + sb)
              // if(element[2] == sb[3])
            }
          }
        }
      } */
    }
  }
}
</script>
