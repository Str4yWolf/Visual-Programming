<template>
  <div class="cosine-similarity">
    <span style="text-align: center;">
      <span style=" padding: 0px 5px 0px 5px">
        <strong>Cosine Similarity</strong> &nbsp; [I/O: Image/Output]
      </span>
      <strong>(Load 2nd Image)</strong>
    </span>
    <br/>
    <q-uploader />
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'CosineSimilarity',
  data () {
    return {
    }
  },
  methods: {
    /*
            Cosine similarity
    */
    compare: function () {
      var r = Math.random()
      if (r > 0.99) {
        r = 1
      }
      alert('Similarity: ' + r)
    },
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from cosine similarity')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .cosine-similarity {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid green;
  background-color: #b3ffb3;
  border-radius: 8px;
}
button .del-btn {
/*  background: red;*/
}
</style>
