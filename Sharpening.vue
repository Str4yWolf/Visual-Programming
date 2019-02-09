<template>
  <div class="sharpening">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Sharpening</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Select Strength)</strong>
    </span>
   <q-slider
      v-model="sharpeningStrength"
      label-always
      :min="0" :max="100"
      :label-value="`${sharpeningStrength}%`"
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
      sharpeningStrength: 55
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
div .sharpening {
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
