<template>
  <div class="img-preview-outer">
    <div style="padding: 15px 0px 0px 30px; font-weight: bold;">
      Image Preview
      <q-icon name="info" size="24px" color="amber" title="Click for more information"
        style="display: inline; padding: 0px 0px 0px 30px;">
        <q-popover>
          <q-card inline style="width: 500px">
            <q-card-title>Image Preview</q-card-title>
            <q-card-main>
              <p>Displays a preview of the image that results from performing your chain
                 of blocks as a program. Hit the <strong>Run Program</strong> button to
                 run your program.
              </p>
            </q-card-main>
          </q-card>
        </q-popover>
      </q-icon>
    </div>
    <div class="img-preview-image">
      <img id="image-preview" src="../statics/dummy.jpg" v-bind:style="{width: pWidth? 3.6*pWidth+'px':'360px'}">
    </div>&nbsp;
          <q-slider
          v-model="zoomSliderPreview"
          @input="val=>{pWidth=val}"
          label-always
          :label-value="`${zoomSliderPreview}%`"
          :min="25"
          :max="250"
          :step="25"
          />
          <button id="btn3" @click="exportingResults()">Export Results</button>
  </div>
</template>

<script>
export default {
  // name: '',
  data () {
    return {
      zoomSliderPreview: 100
    }
  },
  created () {
    // listen to event calls from elsewhere
    this.$root.$on('updateView', this.updateView)
  },
  methods: {
    /*
            Updates the image in the preview(s) according to which blocks are connected
            to the starting block
            @params: Array(String) blocks
    */
    updateView: function (blocks) {
      if (blocks.includes('lettersClassificationBlock')) {
        var text = document.getElementById('input-lettersClassification').value.toLowerCase()
        // Why does Vue not update correct pictures even though ...
        // ... Branches are entered correctly
        // ... Format extension is correct
        // ... Paths match up (copy and paste)
        // ... Similar image display works with cosine similarity
        // Don't know why it doesn't work
        if (text === 'japanese') {
          console.log('entered japanese branch')
          this.setImage('../statics/dummy_output_japanese.jpg')
        } else if (text === 'latin') {
          console.log('entered latin branch')
          this.setImage('../statics/dummy_output_latin.jpg')
        } else {
          console.log('entered else branch')
          this.$root.$emit('notify', 'Could not classify letters!', 'negative')
          this.setImage('../statics/void.jpg')
          return
        }
      }
      if (blocks.includes('cosineSimilarityBlock')) {
        this.setImage('../statics/dummy_output_cosine_similarity.jpg')
        return
      }
      // permutations to keep track
      // 1,2,3
      if (blocks.includes('binarizationBlock') &&
        blocks.includes('rotationBlock') &&
        blocks.includes('clusteringBlock')) {
        this.setImage('../statics/dummy_binarized_rotated_clustered.jpg')
        return
      }
      // 1,2
      if (blocks.includes('binarizationBlock') &&
        blocks.includes('rotationBlock')) {
        this.setImage('../statics/dummy_binarized_rotated.jpg')
        return
      }
      // 1,3
      if (blocks.includes('binarizationBlock') &&
        blocks.includes('clusteringBlock')) {
        this.setImage('../statics/dummy_binarized_clustered.jpg')
        return
      }
      // 2,3
      if (blocks.includes('rotationBlock') &&
        blocks.includes('clusteringBlock')) {
        this.setImage('../statics/dummy_rotated_clustered.jpg')
        return
      }
      // 1
      if (blocks.includes('binarizationBlock')) {
        this.setImage('../statics/dummy_binarized.jpg')
        return
      }
      // 2
      if (blocks.includes('rotationBlock')) {
        this.setImage('../statics/dummy_rotated.jpg')
        return
      }
      // 3
      if (blocks.includes('clusteringBlock')) {
        this.setImage('../statics/dummy_clustered.jpg')
      } else {
        this.setImage('../statics/dummy.jpg')
      }
    },
    /*
            Sets the image according to the path
            @params: String path
    */
    setImage: function (path) {
      document.getElementById('image-preview').src = path
    },
    exportingResults: function () {
      var div = document.getElementById('image-preview')
      div.border = '2px solid red'
      this.$root.$emit('notify', 'Proceeding with exporting results.', 'info')
    }
  }
}
</script>

<style>
div .img-preview-outer {
  border: 2px solid black;
  height: 520px;
  width: 400px;
  background: #fae5d3;
  z-index: 6;
}
div .img-preview-image {
  border: none;
  position: relative;
  height: 320px;
  width: 360px;
  top: 25px;
  left: 25px;
  background: white;
  overflow: scroll;
  z-index: 7;
}
#btn3 {
  position: relative;
  font-weight: bold;
  width: 155px;
  height: 50px;
  top: 0px;
  right: 25px;
  left: 25px;
  margin: 10px;
  z-index: 7;
}
/*previous version without zoom slider
  div .img-preview-outer {
  border: 2px solid black;
  height: 500px;
  width: 400px;
  background: #fae5d3;
  z-index: 6;
}
div .img-preview-image {
  border: none;
  position: relative;
  max-height: 400px;
  max-width: 350px;
  top: 25px;
  left: 25px;
  background: white;
  overflow: hidden;
  z-index: 7;
}*/
</style>
