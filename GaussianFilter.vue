<template>
  <div class="gaussian-filter">
    <span style="text-align: center;">
      <span style=" padding: 0px 15px 0px 15px">
        <strong>Gaussian Filter</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Select Sigma)</strong>
    </span>
    <q-slider
      v-model="gaussianSTD"
      :min="0"
      :max="5"
      :step="0.05"
      label-always
    />
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
      gaussianSTD: 1.5
    }
  },
  methods: {
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
div .gaussian-filter {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid blue;
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
