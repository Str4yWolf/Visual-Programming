<!-- TODO:
  docking/undocking and how it works together with delete
  update of links and connected blocks also upon delete
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
      // binarizationBlocks: [],
      blocks: {binarizationBlocks: [[100, 100], [100, 200]]},
      // these are the links or docks between blocks
      linksTop: [],
      linksBottom: [],
      // connected blocks (value) of a block (key)
      connectedBlocks: [],
      // show notifications to user
      showNotifications: true,
      // whether you can dock again
      redockable: true,
      // what data can be input to each block
      intype: {binarizationBlock: 'image'},
      // what data will be the output of each block
      outtype: {binarizationBlock: 'image'},
      // whether a block is incompatible
      incompatible: false
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
        this.blocks.binarizationBlocks.push([this.initialPos[0], this.initialPos[1]])
        // this.binarizationBlocks.push([this.initialPos[0], this.initialPos[1]])
        if (this.showNotifications) {
          alert('Binarization component #' + (this.blocks.binarizationBlocks.length) + ' added')
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
      // move all blocks connected to the current block
      this.moveConnectedBlocks(ref1, event.delta.x, event.delta.y)
      if (typeof this.$refs[ref1].$el === 'undefined') {
        bB1 = this.$refs[ref1][0].$el.getBoundingClientRect()
      } else {
        bB1 = this.$refs[ref1].$el.getBoundingClientRect()
      }
      Object.entries(this.blocks).forEach(blockType => {
        Object.entries(blockType[1]).forEach(block => {
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
            var overlap = !(bB1.right < bB2.left ||
                            bB1.left > bB2.right ||
                            bB1.bottom < bB2.top ||
                            bB1.top > bB2.bottom)
            // dockable bB1 that you're moving to the bottom of bB2
            var dockable1 = overlap && ((bB2.bottom - 10) < bB1.top)
            if (this.redockable && dockable1 &&
                !this.linksBottom.includes(ref1) &&
                !this.linksTop.includes(ref2)) {
              var dock1 = confirm('Do you want to dock ' + ref1 + ' to ' + ref2 + '?')
              if (dock1) {
                this.dock(ref2, ref1)
              }
            }
            // reverse case
            var dockable2 = overlap && ((bB1.bottom - 10) < bB2.top)
            if (this.redockable && dockable2 &&
                !this.linksBottom.includes(ref2) &&
                !this.linksTop.includes(ref1)) {
              var dock2 = confirm('Do you want to dock ' + ref2 + ' to ' + ref1 + '?')
              if (dock2) {
                this.dock(ref1, ref2)
              }
            }
            // avoid asking the user again if still overlapping
            this.redockable = false
            if (!overlap) {
              this.redockable = true
            }
          }
        })
      })
    },
    /*
            move all blocks connected to b in response to a change in position
    */
    moveConnectedBlocks: function (b, x, y) {
      console.log('Called moveConnectedBlocks')
      /*
      // connected blocks
      // console.log(b)
      if (!Object.values[b]) {
        console.log('cbs undefined')
        return
      }
      var cbs = Object.values(this.connectedBlocks[b])
      console.log(cbs)
      for (var i = 0; i < cbs.length; i++) {
        var arr = cbs[i].split('-')
        var blockType = arr[0].substring(0, arr[0].length) + 's'
        var index = arr[1]
        // console.log(blockType)
        // console.log(index)
        this.$set(this.blocks[blockType][index], 0, this.blocks[blockType][index] + x)
        this.$set(this.blocks[blockType][index], 1, this.blocks[blockType][index] + y)
      }
      */
      for (var i = 0; i < this.connectedBlocks.length; i++) {
        // first element is block itself, other elements connected ones
        var keyVals = this.connectedBlocks[i].split(' ')
        // console.log('keyVals: ' + keyVals)
        // console.log('typeof keyVals: ' + typeof keyVals)
        // console.log('length of keyVals: ' + keyVals.length)
        if (keyVals[0] === b) {
          for (var j = 1; j < keyVals.length; j++) {
            // connected block
            var cb
            if (typeof this.$refs[keyVals[j]].$el === 'undefined') {
              cb = this.$refs[keyVals[j]][0].$el
            } else {
              cb = this.$refs[keyVals[j]].$el
            }
            cb.style.left = (parseInt(cb.style.left) + x) + 'px'
            cb.style.top = (parseInt(cb.style.top) + y) + 'px'
            // console.log('cb: ' + cb)
            // console.log('Connected block ' + keyVals[j])
            // console.log(keyVals[j] + 'x: ' + cb[0])
            // console.log(keyVals[j] + 'y: ' + cb[1])
            // this.$set(cb, 0, cb[0] + x)
            // this.$set(cb, 1, cb[1] + y)
            // var arr = cb.id.split('-')
            // var blockType = arr[0].substring(0, arr[0].length) + 's'
            // var index = arr[1]
            // console.log(b)
            // console.log(cb)
            // console.log(blockType)
            // console.log(index)
            // this.$set(this.blocks[blockType][index], 0, this.blocks[blockType][index] + x)
            // this.$set(this.blocks[blockType][index], 1, this.blocks[blockType][index] + y)
            // cb.style.left = this.blocks[blockType][index][0] + x + 'px'
            // cb.style.top = this.blocks[blockType][index][1] + y + 'px'
          }
        }
      }
    },
    /*
            docks the block
    */
    dock: function (b1, b2) {
      this.linksTop.push(b1)
      this.linksBottom.push(b2)
      if (this.showNotifications) {
        alert('Docked.')
      }
      this.updateConnected(b1)
      this.updateConnected(b2)
      // console.log(this.links)
      // console.log(typeof this.links)
      // console.log(Object.keys(this.links))
      // console.log(Object.values(this.links))
    },
    /*
            updates which blocks are connected to b
    */
    updateConnected: function (b) {
      // console.log('called updateConnected')
      // blocks connected to b besides itself
      var connected = b
      for (var i = 0; i < this.linksTop.length; i++) {
        if (this.linksTop[i] === b) {
          // console.log('pushed updateConnected')
          connected = connected.concat(' ' + this.linksBottom[i])
        }
        if (this.linksBottom[i] === b) {
          // console.log('pushed updateConnected')
          connected = connected.concat(' ' + this.linksTop[i])
        }
      }
      // console.log('updatedConnected connected: ' + connected)
      console.log('updatedConnected this.connectedBlocks before: ' + this.connectedBlocks)
      // overwrite old entry if there exists one
      // for (var j = 0; j < this.connectedBlocks.length; j++) {
      //   if (this.connectedBlocks[j][0] === b) {
      //     this.connectedBlocks[j] = connected
      //     console.log('updatedConnected this.connectedBlocks after: ' + this.connectedBlocks)
      //   return
      //   }
      // }
      this.connectedBlocks.push(connected)
      // create new entry if necessary
      // this.connectedBlocks.push({key: b, value: connected})
      console.log('updatedConnected this.connectedBlocks after: ' + this.connectedBlocks)
    }
  }
}
</script>
