<!-- TODO:
  fix interblock reference error: every block reads from
  one single input field only (wrong get element by Id)
-->
<template>
  <div class="clustering">
    <span style="text-align: center; font-weight: bold;">Clustering</span>
    <br/><br/>
    <em>Choose Method &nbsp; &nbsp;</em>
    <button @click="cluster">KNN</button>
    <button @click="cluster">DBScan</button>
    <button @click="cluster">k-means</button>
    <button @click="cluster">spectral</button>
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'Clustering',
  data () {
    return {
    }
  },
  methods: {
    /*
            Clusters image accoring to threshold
    */
    cluster: function () {
      alert('Image clustered.')
    },
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from clustering')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .clustering {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid red;
  background-color: #ff9999;
  border-radius: 8px;
}
button .del-btn {
  background: red;
}
</style>
