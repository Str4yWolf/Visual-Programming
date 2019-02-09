<template>
  <div class="greyscaling">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Greyscaling</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Select Channels)</strong>
    </span>
    <br>
    <br>
    <q-checkbox style="padding: 0px 30px 0px 30px;" v-model="rgb1" val="red" label="Red" />
    <q-checkbox style="padding: 0px 30px 0px 30px;" v-model="rgb2" val="green" label="Green" />
    <q-checkbox style="padding: 0px 30px 0px 30px;" v-model="rgb3" val="blue" label="Blue" />
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'greyscaling',
  data () {
    return {
      rgb1: true,
      rgb2: true,
      rgb3: true
    }
  },
  methods: {
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from greyscaling')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .greyscaling {
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
