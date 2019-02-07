<template>
  <div class="lettersClassification">
    <span style="text-align: center;">
      <span style=" padding: 0px 10px 0px 10px">
        <strong>LettersClassification</strong> &nbsp; [I/O: Image/Text]
      </span>
      <strong>(Enter Alphabet)</strong>
    </span>
    <br/>
    <br/>
    <input id="input-lettersClassification">
    <button @click="classify">Classify</button>
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'LettersClassification',
  data () {
    return {
    }
  },
  methods: {
    /*
            classifies letters given an alphabet
    */
    classify: function () {
      var alphabet = document.getElementById('input-lettersClassification').value
      if (alphabet === 'Japanese') {
        alert('Classified letters (Japanese): "転生したらスライムだった件"')
      } else if (alphabet === 'Latin') {
        alert('Classified letters (Latin): "tensei shitara suraimu datta ken"')
      } else {
        alert('Could not classify letters.')
      }
    },
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from lettersClassification')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .lettersClassification {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid orange;
  background-color:  #f7dc6f ;
  border-radius: 8px;
}
div .deletion {
  position: absolute;
  top: 5px;
  right: 5px;
  color: black;
  background: red;
  font-weight: bold;
  padding: 2px;
}
button .del-btn {
/*  background: red;*/
}
</style>
