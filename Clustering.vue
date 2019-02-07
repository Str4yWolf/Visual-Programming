<template>
  <div class="clustering">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Clustering</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Choose Method)</strong>
    </span>
    <div class="q-btn-toggle">
    <q-btn-toggle
      v-model="clusteringChoices"
      color="red"
      toggle-color="green"
      :options="[
        {label: 'KNN', value: 'KNN'},
        {label: 'DBScan', value: 'DBScan'},
        {label: 'K-Means', value: 'K-Means'},
        {label: 'Spectral', value: 'Spectral'}
      ]"
      push
      glossy
      size="14px"
    /></div>
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
div .q-btn-toggle {
  position: absolute;
  top: 25px;
  left: 40px;
}
div .clustering {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid red;
  background-color: #ff9999;
  border-radius: 8px;
}
button .del-btn {
/*  background: red;*/
}
</style>
