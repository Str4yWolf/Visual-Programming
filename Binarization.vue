<template>
  <div class="binarization">
    <span style="text-align: center; font-weight: bold;">Binarization</span>
    <br/><br/>
    <em>Enter Threshold &nbsp; &nbsp;</em>
    <input v-model="number" id="input">
    <button @click="binarize">Binarize</button>
   </div>
</template>

<script>
export default {
  // name: 'Binarization',
  data () {
    return {
      blocktype: 'image',
      // What blocktypes can be input
      intype: 'image',
      // What blocktypes can be output
      outtype: 'image'
    }
  },
  methods: {
    binarize: function () {
      var threshold = document.getElementById('input').value
      if (isNaN(threshold)) {
        alert('Please enter an integer.')
      } else if ((threshold < 0) || (threshold > 255)) {
        alert('Please enter an integer between 0 and 255.')
      } else {
        alert('Image binarized.')
      }
    }
  }
}
</script>

<style>
div .binarization {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 2px solid black;
  background-color: powderblue;
}
</style>
