<template>
  <div class="rotation">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Rotation</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Select Degrees)</strong>
    </span>
    <q-slider
      v-model="rotdegs"
      :min="-180"
      :max="180"
      :step="1"
      label-always
    />
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'rotation',
  data () {
    return {
      rotdegs: 0
    }
  },
  methods: {
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from rotation')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .rotation {
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
