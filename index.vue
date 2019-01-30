<!-- TODO:
  selection frame
  emulate results
  fix red border after elements are docked and overlapping
  (addBlock: replace id with $ref) - failed attempt
  (moveConnected: try $set instead of $el.style) - failed attempt
  (make blocks move smoothly together - tried out everything in my might)
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
    <letters-classification
      @emitted="receiveData"
      v-touch-pan="moveBlock" class="movable q-py-xl"
      :id="'lettersClassificationBlock-'+(i-1)"
      :ref="'lettersClassificationBlock-'+(i-1)"
      :style="{'left': blocks.lettersClassificationBlocks[i-1][0] + 'px',
               'top': blocks.lettersClassificationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.lettersClassificationBlocks.length"
      :key="'lettersClassificationBlock'+i">
    </letters-classification>
    <cosine-similarity
      @emitted="receiveData"
      v-touch-pan="moveBlock" class="movable q-py-xl"
      :id="'cosineSimilarityBlock-'+(i-1)"
      :ref="'cosineSimilarityBlock-'+(i-1)"
      :style="{'left': blocks.cosineSimilarityBlocks[i-1][0] + 'px',
               'top': blocks.cosineSimilarityBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.cosineSimilarityBlocks.length"
      :key="'cosineSimilarityBlock'+i">
    </cosine-similarity>
    <clustering
      @emitted="receiveData"
      v-touch-pan="moveBlock" class="movable q-py-xl"
      :id="'clusteringBlock-'+(i-1)"
      :ref="'clusteringBlock-'+(i-1)"
      :style="{'left': blocks.clusteringBlocks[i-1][0] + 'px',
               'top': blocks.clusteringBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.clusteringBlocks.length"
      :key="'clusteringBlock'+i">
    </clustering>
    <rectangle-select class="select-comp"></rectangle-select>
    <!-- <edit-frame class="blocks_editor"></edit-frame> -->
    </q-page>
</template>

<style>
.movable {
  display: inline-block;
  padding: 0px;
  position: absolute;
  z-index: 1;
}
.select-comp {
  position: fixed;
  top: 0px;
  right: 0px;
  z-index: 0;
}
</style>

<script>
import Binarization from '../components/Binarization.vue'
import LettersClassification from '../components/LettersClassification.vue'
import RectangleSelect from '../components/RectangleSelect.vue'
import CosineSimilarity from '../components/CosineSimilarity.vue'
import Clustering from '../components/Clustering.vue'
// import EditFrame from '../components/editFrame.vue'
export default {
  name: 'PageIndex',
  components: {
    Binarization,
    LettersClassification,
    CosineSimilarity,
    Clustering,
    RectangleSelect
    // EditFrame
  },
  data () {
    return {
      // initial position of new blocks
      initialPos: [100, 100],
      // all blocks
      blocks: {binarizationBlocks: [],
        lettersClassificationBlocks: [],
        cosineSimilarityBlocks: [],
        clusteringBlocks: []},
      // linksTop[i] and linksBottom[i] are connected blocks
      linksTop: [],
      linksBottom: [],
      // connected blocks (value) of a block (key)
      connectedBlocks: {},
      // show notifications to user
      showNotifications: false,
      // whether a block is redockable after docking attempt
      redockable: true,
      // input data type for each block type
      intype: {binarization: 'image',
        lettersClassification: 'image',
        cosineSimilarity: 'image',
        clustering: 'image',
        rectangleSelect: 'image'},
      // output data type for each block type
      outtype: {binarization: 'image',
        lettersClassification: 'text',
        cosineSimilarity: 'none',
        clustering: 'image',
        rectangleSelect: 'image'}
    }
  },
  created () {
    // listen to event calls from elsewhere
    this.$root.$on('addBlock', this.addBlock)
    this.$root.$on('resetAll', this.resetAll)
    this.$root.$on('toggleNotifications', () => {
      this.showNotifications = !this.showNotifications
    })
  },
  methods: {
    /*
            Receives data[message, object] from child components and passes on data according to message
            @params: Array data[String message, Object object]
    */
    receiveData: function (data) {
      // console.log('received data')
      if (data[0] === 'deleteBlock') {
        this.deleteBlock(data[1])
      }
    },
    /*
            Adds a block of the type specified. Initial positions given in data field.
            @params: String blockName
    */
    addBlock: function (blockName) {
      var blockArray = blockName + 'Blocks'
      var blockIndex = this.blocks[blockArray].length
      var ref = blockName + 'Block-' + blockIndex
      this.blocks[blockArray].push([this.initialPos[0], this.initialPos[1]])
      console.log(ref)
      /*
      var blockId
      if (typeof this.$refs[ref].$el === 'undefined') {
        blockId = this.$refs[ref][0].$el
      } else {
        blockId = this.$refs[ref].$el
      }
      console.log(blockId)
      */
      var blockId = ref
      this.connectedBlocks[blockId] = [] // entry for connected blocks
      if (this.showNotifications) {
        alert('created ' + blockName + 'block #' + (blockIndex + 1) + ' at coordinates ' + this.initialPos)
      }
    },
    /*
            Deletes a block specified in data.
            @params: Object data
    */
    deleteBlock: function (data) {
      // console.log('called deleteBlock from Index')
      if (this.showNotifications) {
        var proceed = confirm('Are you sure you would like to delete this component? ' +
                              'This action cannot be undone.')
        if (!proceed) {
          return
        }
      }
      var ref = data.$el.id
      var parentArray = ref.split('-')[0] + 's'
      var index = parseInt(ref.split('-')[1])
      // delete all links
      for (var i = this.linksTop.length - 1; i >= 0; i--) {
        if (this.linksTop[i] === ref) {
          // update the connected block at bottom
          var linkBottom = this.linksBottom[i]
          // delete entries
          console.log('delete top===ref this.linksTop before: ' + this.linksTop)
          this.linksTop.splice(i, 1)
          this.linksBottom.splice(i, 1)
          console.log('delete top===ref this.linksTop after: ' + this.linksTop)
          this.updateConnected(linkBottom)
        }
        if (this.linksBottom[i] === ref) {
          // update the connected block at top
          var linkTop = this.linksTop[i]
          // delete entries
          console.log('delete bottom===ref this.linksTop before: ' + this.linksTop)
          this.linksTop.splice(i, 1)
          this.linksBottom.splice(i, 1)
          console.log('delete bottom===ref this.linksTop after: ' + this.linksTop)
          this.updateConnected(linkTop)
        }
      }
      // delete block itself and its dictionary entry
      this.$delete(this.blocks[parentArray], index)
      delete this.connectedBlocks[ref]
    },
    /*
            Find out which element is moving (adapted from Vinodh's reference on Stine).
            @params: Event event
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
            Move the block which has triggered the event.
            @params: Event event
    */
    moveBlock: function (event) {
      // [blockTypeName, index] of block which triggered event
      var sRef1 = this.getActiveElement(event)
      // name of parent array and index
      var blockArray = sRef1[0] + 's'
      var index = parseInt(sRef1[1])
      // console.log(element[0] + ' #' + blockNumber + ' with index ' + index + ' is moving')
      // get new positions and update
      var newX = this.blocks[blockArray][index][0] + event.delta.x
      var newY = this.blocks[blockArray][index][1] + event.delta.y
      this.$set(this.blocks[blockArray], index, [newX, newY])
      // bounding box, element, and reference
      var bB1
      var el1
      var ref1 = sRef1[0] + '-' + index
      // move all blocks connected to the current block
      this.moveConnectedBlocks(ref1, [event.delta.x, event.delta.y])
      // either one should work
      if (typeof this.$refs[ref1].$el === 'undefined') {
        el1 = this.$refs[ref1][0].$el
      } else {
        el1 = this.$refs[ref1].$el
      }
      bB1 = el1.getBoundingClientRect()
      // search for other blocks iteratively
      Object.entries(this.blocks).forEach(blockType => { // block types
        Object.entries(blockType[1]).forEach(block => { // instances of each type
          if (block[1] !== this.blocks[blockArray][index]) { // excluding block which is moving
            var bB2
            var el2
            // reconstruct 'blockTypeName-index', and its split array version
            var ref2 = blockType[0].substring(0, blockType[0].length - 1) + '-' + block[0]
            var sRef2 = ref2.split('-')
            // either one should work
            if (typeof this.$refs[ref2].$el === 'undefined') {
              el2 = this.$refs[ref2][0].$el
            } else {
              el2 = this.$refs[ref2].$el
            }
            bB2 = el2.getBoundingClientRect()
            // get overlapping areas
            var overlap = !(bB1.right < bB2.left ||
                            bB1.left > bB2.right ||
                            bB1.bottom < bB2.top ||
                            bB1.top > bB2.bottom)
            // get the types of each block by name
            var type1 = sRef1[0].substring(0, sRef1[0].length - 5)
            var type2 = sRef2[0].substring(0, sRef2[0].length - 5)
            // output(ref2) compatible with input(ref1), and vice versa
            var compatible1 = this.outtype[type2] === this.intype[type1]
            var compatible2 = this.outtype[type1] === this.intype[type2]
            // checking for dockability of block (ref1) moving to the bottom of ref2
            var dockable1 = overlap && ((bB2.bottom - 10) < bB1.top)
            if (this.redockable && compatible1 && dockable1 &&
                !this.linksBottom.includes(ref1) && !this.linksTop.includes(ref2)) {
              var dock1 = confirm('Do you want to dock ' + ref1 + ' to ' + ref2 + '?')
              if (dock1) {
                this.dock(ref2, ref1)
                compatible1 = true
                compatible2 = true
              }
            }
            // reverse case
            var dockable2 = overlap && ((bB1.bottom - 10) < bB2.top)
            if (this.redockable && compatible2 && dockable2 &&
                !this.linksBottom.includes(ref2) && !this.linksTop.includes(ref1)) {
              var dock2 = confirm('Do you want to dock ' + ref2 + ' to ' + ref1 + '?')
              if (dock2) {
                this.dock(ref1, ref2)
                compatible1 = true
                compatible2 = true
              }
            }
            // avoid asking user to dock again if still overlapping
            this.redockable = false
            var bothDocked = (this.linksBottom.includes(ref2) && this.linksTop.includes(ref1)) || (this.linksBottom.includes(ref1) && this.linksTop.includes(ref2))
            // display incompatibility of blocks - style 1 (outset red border)
            if (overlap && (!compatible1 || !compatible2) && !bothDocked) {
              el1.style.height = '120px'
              el1.style.width = '520px'
              el1.style.border = '12px solid red'
            }
            if (!overlap) {
              this.redockable = true
              el1.style.height = '100px'
              el1.style.width = '500px'
              el1.style.border = '2px solid black'
            }
            /*
            // display incompatibility of blocks - style 2 (inset red border)
            if (overlap && (!compatible1 || !compatible2)) {
              el1.style.border = '10px solid red'
            }
            if (!overlap) {
              this.redockable = true
              el1.style.border = '2px solid grey'
            }
            */
          }
        })
      })
    },
    /*
            Move all blocks connected to block b in response to a change in position delta
            @params: String b (block), Array delta[int x, int y]
    */
    moveConnectedBlocks: function (b, delta) {
    // b not connected to any other blocks
      if (!this.connectedBlocks[b]) {
        return
      }
      var cbs = this.connectedBlocks[b]
      // console.log('connected to ' + b + ': ' + cbs)
      for (var i = 0; i < cbs.length; i++) {
        // set by attribute - properly called but inexplicably bad
        var ref
        if (cbs[i].charAt(0) === ' ') {
          ref = cbs[i].substring(1, cbs[i].length)
        } else {
          ref = cbs[i]
        }
        var cb
        console.log('moveConnected with ' + b + ' and current connected block ' + ref)
        if (typeof this.$refs[ref].$el === 'undefined') {
          cb = this.$refs[ref][0].$el
        } else {
          cb = this.$refs[ref].$el
        }
        cb.style.left = (parseInt(cb.style.left) + delta[0]) + 'px'
        cb.style.top = (parseInt(cb.style.top) + delta[1]) + 'px'
        /*
        // set by array - $set doesn't work at all for some reason
        var arr = cbs[i].split('-')
        var blockType = arr[0].substring(1, arr[0].length) + 's'
        var index = arr[1]
        console.log(blockType)
        console.log(index)
        this.$set(this.blocks[blockType][index], 0, this.blocks[blockType][index] + delta[0])
        this.$set(this.blocks[blockType][index], 1, this.blocks[blockType][index] + delta[1])
        */
      }
    },
    /*
            Docks the blocks b1 (top) and b2 (bottom).
            @params: String b1, String b2
    */
    dock: function (b1, b2) {
      this.linksTop.push(b1)
      this.linksBottom.push(b2)
      if (this.showNotifications) {
        alert('Docked.')
      }
      this.updateConnected(b1)
      this.updateConnected(b2)
    },
    /*
            Updates which blocks are connected to block b.
            @params: String b
    */
    updateConnected: function (b) {
      // find blocks connected to b
      var connected = []
      for (var i = 0; i < this.linksTop.length; i++) {
        if (this.linksTop[i] === b) {
          console.log('pushed updateConnected')
          connected.push(this.linksBottom[i])
        }
        if (this.linksBottom[i] === b) {
          console.log('pushed updateConnected')
          connected.push(' ' + this.linksTop[i])
        }
      }
      this.connectedBlocks[b] = connected
    },
    /*
            Resets everything.
    */
    resetAll: function () {
      console.log('called resetAll in Index')
      var reset = confirm('Are you sure you want to reset everything? This action cannot be undone.')
      if (reset) {
        this.initialPos = [100, 100]
        this.blocks = {binarizationBlocks: [], lettersClassificationBlocks: []}
        this.linksTop = []
        this.linksBottom = []
        this.blocks = {binarizationBlocks: [],
          lettersClassificationBlocks: [],
          cosineSimilarityBlocks: [],
          clusteringBlocks: []}
        this.showNotifications = true
        this.redockable = true
        this.incompatible = false
      }
    },
    /*
            sets the initial positions of blocks the parameters
    */
    setInitialPos: function (x, y) {
      this.initialPos = [x, y]
    }
  }
}
</script>
<style>
.flex {
  background: #d3d3d3;
  z-index: 0;
}
</style>
