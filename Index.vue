<!-- TODO:
  docking/undocking and how it works together with delete
  selection frame
  emulate results
  -->
<template>
  <q-page class="flex flex-center">
    <binarization
      @emitted="receiveData"
      v-touch-pan="moveBlock" class="movable q-py-xl"
      :id="'binarizationBlock-'+(i-1)"
      :ref="'binarizationBlock-'+(i-1)"
      :style="{'left': blocks.binarizationBlocks[i-1][0] + 'px',
               'top': blocks.binarizationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.binarizationBlocks.length"
      :key="'binarizationBlock'+i">
    </binarization>
    <rectangle-select class="select-comp"></rectangle-select>
    <edit-frame class="blocks_editor"></edit-frame>
    </q-page>
</template>

<style>
#notifications {
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: 10;
}
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
      // binarizationBlocks: [],
      blocks: {binarizationBlocks: []},
      // these are the links or docks between blocks
      links: [],
      // show notifications to user
      showNotifications: true
    }
  },
  created () {
    this.$root.$on('addBlock', this.addBlock)
    this.$root.$on('toggleNotifications', () => {
      this.showNotifications = !this.showNotifications
    })
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
        this.blocks.binarizationBlocks.push([this.initialPos[0], this.initialPos[1],
          'image', 'image'])
        // this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1],
        // 'image', 'image'])
        if (this.showNotifications) {
          alert('Binarization component #' + this.binarizationCounter + ' added')
        }
        console.log('created ' + blockName + 'Block #' + this.binarizationCounter + ' at coordinates ' + this.initialPos)
      }
    },
    /*
            deletes a block which called this function
    */
    deleteBlock: function (data) {
      console.log('called deleteBlock from Index')
      if (this.showNotifications) {
        var proceed = confirm('Are you sure you would like to delete this component? ' +
                              'This action cannot be undone.')
        if (!proceed) {
          return
        }
      }
      var parentArray = data.$el.id.split('-')[0] + 's'
      var index = parseInt(data.$el.id.split('-')[1])
      this.$delete(this.blocks[parentArray], index)
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
      // var blockNumber = index + 1
      // console.log(element[0] + ' #' + blockNumber +
      //            ' with index ' + index + ' is moving')
      // update positions
      var newX = this.blocks[blockArray][index][0] + event.delta.x
      var newY = this.blocks[blockArray][index][1] + event.delta.y
      // console.log(newX, newY)
      this.$set(this.blocks[blockArray], index, [newX, newY])
      var bB1
      var ref1 = element[0] + '-' + index
      if (typeof this.$refs[ref1].$el === 'undefined') {
        bB1 = this.$refs[ref1][0].$el.getBoundingClientRect()
      } else {
        bB1 = this.$refs[ref1].$el.getBoundingClientRect()
      }
      // console.log('ref1: ' + ref1)
      // console.log(typeof ref1)
      // console.log('bB1: ' + bB1)
      // console.log(typeof bB1)
      // console.log(this.blocks)
      // console.log(typeof this.blocks)
      // console.log('Coordinates of ' + ref1 + '\n' +
      //              '      top-left corner: (' + bB1.left + ', ' + bB1.top + ')\n' +
      //              '  bottom-right corner: (' + bB1.right + ', ' + bB1.bottom + ')')
      Object.entries(this.blocks).forEach(blockType => {
        // console.log(blockType[0])
        // console.log(typeof blockType[0])
        Object.entries(blockType[1]).forEach(block => {
          // console.log(block[1])
          // console.log(typeof block[1])
          if (block[1] !== this.blocks[blockArray][index]) {
            var bB2
            // the name (key) and index (array key) of a block
            var ref2 = blockType[0].substring(0, blockType[0].length - 1) +
                       '-' + block[0]
            if (typeof this.$refs[ref2].$el === 'undefined') {
              // bB2 = this.blocks[blockType][block][1].$refs[ref2].$el.getBoundingClientRect()
              bB2 = this.$refs[ref2][0].$el.getBoundingClientRect()
            } else {
              bB2 = this.$refs[ref2].$el.getBoundingClientRect()
            }
            // console.log('ref2: ' + ref2)
            // console.log(typeof ref2)
            // console.log('bB2: ' + bB2)
            // console.log(typeof bB2)
            //
            var overlap = !(bB1.right < bB2.left ||
                            bB1.left > bB2.right ||
                            bB1.bottom < bB2.top ||
                            bB1.top > bB2.bottom)
            // if (overlap) {
            //   console.log(ref1 + ' collided with ' + ref2)
            // }
            // dockable bB1 that you're moving to the bottom of bB2
            var dockable = overlap && (bB1.top === bB2.bottom)
            if (dockable &&
                !Object.values(this.links).includes(ref1) &&
                !Object.keys(this.links).includes(ref2)) {
              var dock = confirm('Do you want to dock ' + ref1 + ' to ' + ref2 + '?')
              if (dock) {
                this.dock(ref2, ref1)
              }
            }
          }
        })
      })
    },
    /*
            docks the block
    */
    dock: function (b1, b2) {
      this.links[b1] = b2
      if (this.showNotifications) {
        alert('Docked.')
      }
      console.log(this.links)
      console.log(typeof this.links)
      console.log(Object.keys(this.links))
      console.log(Object.values(this.links))
    }
  }
}
</script>
