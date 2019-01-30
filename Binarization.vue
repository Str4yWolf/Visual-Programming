<!-- TODO:
  fix interblock reference error: every block reads from
  one single input field only (wrong get element by Id)
-->
<template>
  <div class="binarization">
    <span style="text-align: center; font-weight: bold;">Binarization</span>
    <br/><br/>
    <em>Enter Threshold &nbsp; &nbsp;</em>
    <input id="input">
    <button @click="binarize">Binarize</button>
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'Binarization',
  data () {
    return {
    }
  },
  methods: {
    /*
            binarizes the image with a threshold
            and filters some inappropriate user inpus
    */
    binarize: function () {
      var threshold = document.getElementById('input').value
      if (isNaN(threshold)) {
        alert('Please enter an integer.')
      } else if ((threshold < 0) || (threshold > 255)) {
        alert('Please enter an integer between 0 and 255.')
      } else {
        alert('Image binarized.')
      }
    },
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from binarization')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .binarization {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 2px solid blue;
  border-radius: 8px;
  background-color: powderblue;
}
div .deletion {
  position: absolute;
  top: 5px;
  right: 5px;
  color: black;
/*  background: red;*/
  font-weight: bold;
  padding: 2px;
}
button .del-btn {
/*  background: red;*/
}
</style>
