<!-- TODO:
  selection frame
  fix red border after elements are docked and overlapping
  -->
<template>
  <q-page class="flex flex-center">
    <binarization
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'binarizationBlock-'+(i-1)"
      :ref="'binarizationBlock-'+(i-1)"
      :style="{'left': blocks.binarizationBlocks[i-1][0] + 'px',
               'top': blocks.binarizationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.binarizationBlocks.length"
      :key="'binarizationBlock'+i">
    </binarization>
    <rotation
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'rotationBlock-'+(i-1)"
      :ref="'rotationBlock-'+(i-1)"
      :style="{'left': blocks.rotationBlocks[i-1][0] + 'px',
               'top': blocks.rotationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.rotationBlocks.length"
      :key="'rotationBlock'+i">
    </rotation>
    <greyscaling
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'greyscalingBlock-'+(i-1)"
      :ref="'greyscalingBlock-'+(i-1)"
      :style="{'left': blocks.greyscalingBlocks[i-1][0] + 'px',
               'top': blocks.greyscalingBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.greyscalingBlocks.length"
      :key="'greyscalingBlock'+i">
    </greyscaling>
    <noise-removal
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'noiseRemovalBlock-'+(i-1)"
      :ref="'noiseRemovalBlock-'+(i-1)"
      :style="{'left': blocks.noiseRemovalBlocks[i-1][0] + 'px',
               'top': blocks.noiseRemovalBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.noiseRemovalBlocks.length"
      :key="'noiseRemovalBlock'+i">
    </noise-removal>
    <sharpening
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'sharpeningBlock-'+(i-1)"
      :ref="'sharpeningBlock-'+(i-1)"
      :style="{'left': blocks.sharpeningBlocks[i-1][0] + 'px',
               'top': blocks.sharpeningBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.sharpeningBlocks.length"
      :key="'sharpeningBlock'+i">
    </sharpening>
    <gaussian-filter
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'gaussianFilterBlock-'+(i-1)"
      :ref="'gaussianFilterBlock-'+(i-1)"
      :style="{'left': blocks.gaussianFilterBlocks[i-1][0] + 'px',
               'top': blocks.gaussianFilterBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.gaussianFilterBlocks.length"
      :key="'gaussianFilterBlock'+i">
    </gaussian-filter>
    <letters-classification
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'lettersClassificationBlock-'+(i-1)"
      :ref="'lettersClassificationBlock-'+(i-1)"
      :style="{'left': blocks.lettersClassificationBlocks[i-1][0] + 'px',
               'top': blocks.lettersClassificationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.lettersClassificationBlocks.length"
      :key="'lettersClassificationBlock'+i">
    </letters-classification>
    <cosine-similarity
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'cosineSimilarityBlock-'+(i-1)"
      :ref="'cosineSimilarityBlock-'+(i-1)"
      :style="{'left': blocks.cosineSimilarityBlocks[i-1][0] + 'px',
               'top': blocks.cosineSimilarityBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.cosineSimilarityBlocks.length"
      :key="'cosineSimilarityBlock'+i">
    </cosine-similarity>
    <clustering
      @emitted="receiveData"
      v-touch-pan="move" class="movable q-py-xl"
      :id="'clusteringBlock-'+(i-1)"
      :ref="'clusteringBlock-'+(i-1)"
      :style="{'left': blocks.clusteringBlocks[i-1][0] + 'px',
               'top': blocks.clusteringBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.clusteringBlocks.length"
      :key="'clusteringBlock'+i">
    </clustering>
    <image-preview
      v-touch-pan="move" class="movable q-py-xl"
      :id="'imagePreviewBlock-'+(i-1)"
      :ref="'imagePreviewBlock-'+(i-1)"
      :style="{'left': blocks.imagePreviewBlocks[i-1][0] + 'px',
               'top': blocks.imagePreviewBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.imagePreviewBlocks.length"
      :key="'imagePreviewBlock'+i"></image-preview>
    <rectangle-select
      v-touch-pan="move" class="movable q-py-xl"
      :id="'rectangleSelectBlock-'+(i-1)"
      :ref="'rectangleSelectBlock-'+(i-1)"
      :style="{'left': blocks.rectangleSelectBlocks[i-1][0] + 'px',
               'top': blocks.rectangleSelectBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.rectangleSelectBlocks.length"
      :key="'rectangleSelectBlock'+i">></rectangle-select>
    <encapsulator
      v-touch-pan="move" class="movable q-py-xl"
      :id="'encapsulatorBlock-'+(i-1)"
      :ref="'encapsulatorBlock-'+(i-1)"
      :style="{'left': blocks.encapsulatorBlocks[i-1][0] + 'px',
               'top': blocks.encapsulatorBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.encapsulatorBlocks.length"
      :key="'encapsulatorBlock'+i">></encapsulator>
    <encapsulation
      v-touch-pan="move" class="movable q-py-xl"
      :id="'encapsulationBlock-'+(i-1)"
      :ref="'encapsulationBlock-'+(i-1)"
      :style="{'left': blocks.encapsulationBlocks[i-1][0] + 'px',
               'top': blocks.encapsulationBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.encapsulationBlocks.length"
      :key="'encapsulationBlock'+i">></encapsulation>
    <for-loop
      v-touch-pan="move" class="movable q-py-xl"
      :id="'forLoopBlock-'+(i-1)"
      :ref="'forLoopBlock-'+(i-1)"
      :style="{'left': blocks.forLoopBlocks[i-1][0] + 'px',
               'top': blocks.forLoopBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.forLoopBlocks.length"
      :key="'forLoopBlock'+i">></for-loop>
    <blocks-start
      v-touch-pan="move" class="movable q-py-xl"
      :id="'blocksStartBlock-'+(i-1)"
      :ref="'blocksStartBlock-'+(i-1)"
      :style="{'left': blocks.blocksStartBlocks[i-1][0] + 'px',
              'top': blocks.blocksStartBlocks[i-1][1] + 'px'}"
      v-for="i in blocks.blocksStartBlocks.length"
      :key="'blocksStartBlock'+i"></blocks-start>
    </q-page>
</template>

<style>
.movable {
  display: inline-block;
  padding: 0px;
  position: absolute;
  z-index: 1;
}
</style>

<script>
import Binarization from '../components/Binarization.vue'
import Rotation from '../components/Rotation.vue'
import Greyscaling from '../components/Greyscaling.vue'
import NoiseRemoval from '../components/NoiseRemoval.vue'
import Sharpening from '../components/Sharpening.vue'
import GaussianFilter from '../components/GaussianFilter.vue'
import Clustering from '../components/Clustering.vue'
import LettersClassification from '../components/LettersClassification.vue'
import CosineSimilarity from '../components/CosineSimilarity.vue'
import ImagePreview from '../components/ImagePreview.vue'
import RectangleSelect from '../components/RectangleSelect.vue'
import Encapsulator from '../components/Encapsulator.vue'
import Encapsulation from '../components/Encapsulation.vue'
import ForLoop from '../components/ForLoop.vue'
import BlocksStart from '../components/BlocksStart.vue'
import { Notify } from 'quasar'
export default {
  name: 'PageIndex',
  components: {
    Binarization,
    Rotation,
    Greyscaling,
    NoiseRemoval,
    Sharpening,
    GaussianFilter,
    Clustering,
    LettersClassification,
    CosineSimilarity,
    ImagePreview,
    RectangleSelect,
    Encapsulator,
    Encapsulation,
    ForLoop,
    BlocksStart,
    Notify
  },
  data () {
    return {
      // initial position of new blocks
      initialPos: [100, 100],
      // all blocks
      blocks: {binarizationBlocks: [],
        rotationBlocks: [],
        greyscalingBlocks: [],
        noiseRemovalBlocks: [],
        sharpeningBlocks: [],
        gaussianFilterBlocks: [],
        lettersClassificationBlocks: [],
        cosineSimilarityBlocks: [],
        clusteringBlocks: [],
        imagePreviewBlocks: [[1200, 452]],
        rectangleSelectBlocks: [[1200, 0]],
        encapsulatorBlocks: [[1050, 50]],
        encapsulationBlocks: [],
        forLoopBlocks: [],
        blocksStartBlocks: [[400, 100]]},
      // linksTop[i] and linksBottom[i] are connected blocks
      linksTop: [],
      linksBottom: [],
      // connected blocks (value) of a block (key)
      connectedBlocks: {blocksStart: []},
      // which encapsulation block (key) maps to which block + its children
      encapsulations: {},
      // show certain data to user
      showNotifications: true,
      showEncapsulator: true,
      // whether a block is redockable after docking attempt
      redockable: true,
      // input data type for each block type
      intype: {binarization: 'image',
        rotation: 'image',
        greyscaling: 'image',
        noiseRemoval: 'image',
        sharpening: 'image',
        gaussianFilter: 'image',
        lettersClassification: 'image',
        cosineSimilarity: 'image',
        clustering: 'image',
        imagePreview: 'preview',
        rectangleSelect: 'preview',
        encapsulator: 'encapsulation',
        encapsulation: 'image',
        forLoop: 'void',
        blocksStart: 'input'},
      // output data type for each block type
      outtype: {binarization: 'image',
        rotation: 'image',
        greyscaling: 'image',
        noiseRemoval: 'image',
        sharpening: 'image',
        gaussianFilter: 'image',
        lettersClassification: 'text',
        cosineSimilarity: 'output',
        clustering: 'image',
        imagePreview: 'preview',
        rectangleSelect: 'preview',
        encapsulator: 'encapsulation',
        encapsulation: 'image',
        forLoop: 'void',
        blocksStart: 'image'}
    }
  },
  created () {
    // listen to event calls from elsewhere
    this.$root.$on('notify', this.notify)
    this.$root.$on('addBlock', this.addBlock)
    this.$root.$on('deleteBlock', this.deleteBlock)
    this.$root.$on('runProgram', this.updateView)
    this.$root.$on('resetAll', this.resetAll)
    this.$root.$on('toggleEncapsulator', this.toggleEncapsulator)
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
        this.notify('Added block.', 'positive')
      }
    },
    /*
            Deletes a block specified in data (either object or already id string)
            @params: Object data
    */
    deleteBlock: function (data) {
      // console.log('called deleteBlock from Index')
      var ref
      console.log('deleteBlock')
      console.log(data)
      console.log(typeof data)
      if (typeof data !== 'string') {
        ref = data.$el.id
      } else {
        ref = data
      }
      console.log(ref)
      console.log(typeof ref)
      var parentArray = ref.split('-')[0] + 's'
      var index = parseInt(ref.split('-')[1])
      // delete link
      for (var i = this.linksTop.length - 1; i >= 0; i--) {
        if (this.linksBottom[i] === ref) {
          var linkTop = this.linksTop[i]
          // delete entries
          this.linksTop.splice(i, 1)
          this.linksBottom.splice(i, 1)
          // update parents' connected blocks
          this.updateConnected(linkTop)
          this.getAllParents(linkTop).forEach(parent => {
            this.updateConnected(parent)
          })
        }
        if (this.linksTop[i] === ref) {
          this.linksTop.splice(i, 1)
          this.linksBottom.splice(i, 1)
        }
      }
      // delete block itself and its dictionary entry
      this.$set(this.blocks[parentArray], index, [-1000, -1000])
      this.connectedBlocks[ref] = []
      if (this.showNotifications) {
        this.notify('Deleted block.', 'negative')
      }
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
    move: function (event) {
      // [blockTypeName, index] of block which triggered event
      var sRef1 = this.getActiveElement(event)
      // name of parent array and index
      var blockArray = sRef1[0] + 's'
      var index = parseInt(sRef1[1])
      // bounding box, element, and reference
      var bB1
      var el1
      var ref1 = sRef1[0] + '-' + index
      // move all blocks connected to the current block
      this.moveBlock(ref1, [event.delta.x, event.delta.y])
      if (this.connectedBlocks[ref1] !== undefined) {
        this.connectedBlocks[ref1].forEach(block => {
          this.moveBlock(block, [event.delta.x, event.delta.y])
        })
      }
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
            // distinguish between normal blocks and special blocks
            var isImagePreview = ((type1 === 'imagePreview') || (type1 === 'rectangleSelect'))
            var isEncapsulator = (type1 === 'encapsulator')
            var isForLoop = (type1 === 'forLoop')
            // checking for dockability of block (ref1) moving to the bottom of ref2
            var dockable1 = overlap && ((bB2.bottom - 10) < bB1.top)
            // special case for the forLoop blocks
            var dockable2 = overlap && ((bB2.left - 10) < bB1.right)
            if (this.redockable && compatible1 && dockable1 &&
                !this.linksBottom.includes(ref1) && !this.linksTop.includes(ref2) && !isImagePreview) {
              this.dock(ref2, ref1)
              compatible1 = true
              compatible2 = true
              // align blocks
              var oldX = this.blocks[blockArray][index][0]
              var oldY = this.blocks[blockArray][index][1]
              var dX = bB2.left - 300 - oldX
              var dY = bB2.top + 50 - oldY
              // (with hook 2) change the number of dY's in relation to one another if the blocks don't match up because
              // Vue will sometimes align blocks according to different inexplicable parameters.
              // Don't know how to fix this
              // alternative 1 (50, 50)
              // alternative 2 (86, 14)
              this.moveBlock(ref1, [dX, dY])
              this.getAllChildren(ref1).forEach(child => {
                this.moveBlock(child, [dX, dY])
              })
            }
            // forLoop
            if (this.redockable && isForLoop && dockable2 &&
                !this.linksBottom.includes(ref1) && !this.linksTop.includes(ref2) && !isImagePreview) {
              this.dock(ref2, ref1)
              compatible1 = true
              compatible2 = true
              // align blocks
              var oldX2 = this.blocks[blockArray][index][0]
              var oldY2 = this.blocks[blockArray][index][1]
              // hook 2
              dX = bB2.left - 450 - oldX2
              dY = bB2.top - 50 - oldY2
              this.moveBlock(ref1, [dX, dY])
            }
            // encapsulate
            if (overlap && (!(type1 === 'encapsulation') && (type2 === 'encapsulator'))) {
              this.encapsulate(ref1)
              return
            }
            // decapsulate
            if (overlap && ((type1 === 'encapsulation') && (type2 === 'encapsulator'))) {
              this.decapsulate(ref1)
              return
            }
            // avoid asking user to dock again if still overlapping
            this.redockable = false
            var bothDocked = (this.linksBottom.includes(ref2) && this.linksTop.includes(ref1)) || (this.linksBottom.includes(ref1) && this.linksTop.includes(ref2))
            // display incompatibility of normal blocks - style 1 (outset red border)
            if (overlap && (!compatible1 || !compatible2) && !bothDocked && !isImagePreview && !isEncapsulator && !isForLoop) {
              el1.style.height = '120px'
              el1.style.width = '520px'
              el1.style.border = '12px solid red'
            }
            // undocking
            var parentIndex = this.linksBottom.indexOf(ref1)
            if ((this.linksTop[parentIndex] === ref2) && !overlap) {
              this.undock(ref2, ref1)
            }
            // don't display incompatibility for normal blocks anymore
            if (!overlap && !isImagePreview && !isEncapsulator && !isForLoop) {
              el1.style.height = '100px'
              el1.style.width = '500px'
              el1.style.border = '2px solid black'
            }
            // original status
            if (!overlap) {
              this.redockable = true
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
            Move a block b in response to a change in position delta
            @params: String b (block), Array delta[int x, int y]
    */
    moveBlock: function (b, delta) {
      var arr = b.split('-')
      var blockArray = arr[0] + 's'
      var index = parseInt(arr[1])
      var newX = this.blocks[blockArray][index][0] + delta[0]
      var newY = this.blocks[blockArray][index][1] + delta[1]
      this.$set(this.blocks[blockArray], index, [newX, newY])
    },
    /*
            Docks the blocks b1 (top) and b2 (bottom).
            @params: String b1, String b2
    */
    dock: function (b1, b2) {
      this.linksTop.push(b1)
      this.linksBottom.push(b2)
      this.updateConnected(b1)
      this.getAllParents(b1).forEach(parent => {
        this.updateConnected(parent)
      })
      if (this.showNotifications) {
        this.notify('Connected blocks. Move lower block to disconnect.', 'positive')
      }
    },
    /*
            Undocks the blocks b1 (top) and b2 (bottom).
            @params: String b1, String b2
    */
    undock: function (b1, b2) {
      for (var i = 0; i < this.linksTop.length; i++) {
        if (this.linksBottom[i] === b2) {
          this.linksTop.splice(i, 1)
          this.linksBottom.splice(i, 1)
          this.updateConnected(b1)
          this.getAllParents(b1).forEach(parent => {
            this.updateConnected(parent)
          })
          break
        }
      }
      if (this.showNotifications) {
        this.notify('Disconnected blocks.', 'negative')
      }
    },
    /*
            Gets all parents of a block b, i.e., those that are connected above
            @params: String b
    */
    getAllParents: function (b) {
      var parents = []
      var currentBlock = b
      var foundParent = true
      while (foundParent) {
        foundParent = false
        for (var i = 0; i < this.linksTop.length; i++) {
          if (this.linksBottom[i] === currentBlock) {
            foundParent = true
            parents.push(this.linksTop[i])
            currentBlock = this.linksTop[i]
            break
          }
        }
      }
      return parents
    },
    /*
            Gets all children of a block b, i.e., those that are connected below
            @params: String b
    */
    getAllChildren: function (b) {
      var children = []
      var currentBlock = b
      var foundChild = true
      while (foundChild) {
        foundChild = false
        for (var i = 0; i < this.linksTop.length; i++) {
          if (this.linksTop[i] === currentBlock) {
            foundChild = true
            children.push(this.linksBottom[i])
            currentBlock = this.linksBottom[i]
            break
          }
        }
      }
      return children
    },
    /*
            Updates which blocks are connected to block b1.
            @params: String b
    */
    updateConnected: function (b) {
      this.connectedBlocks[b] = this.getAllChildren(b)
    },
    updateView: function () {
      var processChain = []
      this.getAllChildren('blocksStartBlock-0').forEach(block => {
        processChain.push(block.split('-')[0])
      })
      if (this.showNotifications) {
        this.notify('Running program.', 'positive')
      }
      this.$root.$emit('updateView', processChain)
      if (this.showNotifications) {
        this.notify('Updated view.', 'positive')
      }
    },
    /*
            Resets everything.
    */
    resetAll: function () {
      console.log('called resetAll in Index')
      var reset = confirm('Are you sure you want to reset everything? This action cannot be undone.')
      if (reset) {
        this.initialPos = [100, 100]
        this.linksTop = []
        this.linksBottom = []
        this.connectedBlocks = {blocksStart: []}
        this.blocks = {binarizationBlocks: [],
          rotationBlocks: [],
          greyscalingBlocks: [],
          noiseRemovalBlocks: [],
          sharpeningBlocks: [],
          gaussianFilterBlocks: [],
          clusteringBlocks: [],
          lettersClassificationBlocks: [],
          cosineSimilarityBlocks: [],
          imagePreviewBlocks: [[1200, 452]],
          rectangleSelectBlocks: [[1200, 0]],
          encapsulatorBlocks: [[1050, 50]],
          encapsulationBlocks: [],
          forLoopBlocks: [],
          blocksStartBlocks: [[400, 100]]}
        this.redockable = true
        this.incompatible = false
      }
    },
    /*
            Restyles the borders of a block (String reference) according to a String newStyle
            which contains the CSS property of the format 'px line-type colour'
            @params: Array(String) blocks, String newStyle
    */
    restyleBorder: function (blocks, newStyle) {
      blocks.forEach(block => {
        var style
        if (typeof this.$refs[block].$el === 'undefined') {
          style = this.$refs[block][0].$el.style
        } else {
          style = this.$refs[block].$el.style
        }
        style.border = newStyle
      })
    },
    /*
            Restyles the witdh and height of a block (String reference)
            according to their respective Strings which contain the CSS property in px
            @params: Array(String) blocks, String newWidth, String newHeight
    */
    restyleSize: function (blocks, newWidth, newHeight) {
      blocks.forEach(block => {
        var style
        if (typeof this.$refs[block].$el === 'undefined') {
          style = this.$refs[block][0].$el.style
        } else {
          style = this.$refs[block].$el.style
        }
        style.width = newWidth
        style.height = newHeight
      })
    },
    /*
            Toggles the visibility of the Encapsulator
    */
    toggleEncapsulator: function () {
      if (this.showEncapsulator) {
        this.moveBlock('encapsulatorBlock-0', [-10000, -10000])
        this.showEncapsulator = false
      } else {
        this.moveBlock('encapsulatorBlock-0', [10000, 10000])
        this.showEncapsulator = true
      }
    },
    /*
            Replaces a chain of blocks with argument block on top of it with a single encapsulation block
            @params: String block
    */
    encapsulate: function (block) {
      // Generate encapsulation block
      this.addBlock('encapsulation')
      // get the ref of the current encapsulation block
      var ref = 'encapsulationBlock-' + (this.blocks.encapsulationBlocks.length - 1)
      // add reference
      this.encapsulations[ref] = block
      // hide old blocks
      this.moveBlock(block, [-10000, -10000])
      this.getAllChildren(block).forEach(child => {
        this.moveBlock(child, [-10000, -10000])
      })
    },
    /*
            Replaces an encapsulation eblock with the chain of blocks it encapsulates
            @params: String block
    */
    decapsulate: function (eblock) {
      // get the top block of the blocks the eblock encapsulates
      var ref = this.encapsulations[eblock]
      // show encapsulated blocks at the position where new blocks will be generated
      var blockType = ref.split('-')[0] + 's'
      var index = ref.split('-')[1]
      var oldPos = this.blocks[blockType][index]
      console.log('decapsulate oldPos: ' + oldPos)
      var dX = this.initialPos[0] - oldPos[0]
      var dY = this.initialPos[1] - oldPos[1]
      this.moveBlock(ref, [dX, dY])
      this.getAllChildren(ref).forEach(child => {
        this.moveBlock(child, [dX, dY])
      })
      this.deleteBlock(eblock)
      this.connectedBlocks[eblock] = []
      if (this.showNotifications) {
        this.notify('Deleted encapsulation block.', 'negative')
      }
      this.encapsulations[eblock] = []
    },
    /*
            sets the initial positions of blocks the parameters
    */
    setInitialPos: function (x, y) {
      this.initialPos = [x, y]
    },
    /*
            Notifies a message msg.
            @params: String msg
    */
    notify: function (msg, msgType) {
      if (this.showNotifications) {
        this.$q.notify({
          message: msg,
          timeout: 3000,
          type: msgType
        })
      }
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
