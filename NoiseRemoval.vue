<template>
  <div class="noise-removal">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Noise Removal</strong> &nbsp; [I/O: Image/Image]
      </span>
      <strong>(Select Values)</strong>
    </span>
    <br>
    <span style="font-size: 14px; padding: 0px 0px 0px 10px"><strong>Radius (px): </strong></span>
    <q-knob
      v-model="noise1"
      :min="0"
      :max="100"
      size="40px"
      color="black"
      track-color="grey"
      line-width="8px"
      :placeholder="'$ ' + noise1 + 'px'"
    />
    <span style="font-size: 14px; padding: 0px 0px 0px 30px"><strong>Strength (%): </strong></span>
    <q-knob
      v-model="noise2"
      :min="0"
      :max="100"
      size="40px"
      color="black"
      track-color="grey"
      line-width="8px"
      :placeholder="'$ ' + noise2"
    />
    <span style="font-size: 14px; padding: 0px 0px 0px 30px"><strong>Threshold (%): </strong></span>
    <q-knob
      v-model="noise3"
      :min="0"
      :max="100"
      size="40px"
      color="black"
      track-color="grey"
      line-width="8px"
      :placeholder="'$ ' + noise3"
    />
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'noiseRemoval',
  data () {
    return {
      noise1: 10,
      noise2: 50,
      noise3: 50
    }
  },
  methods: {
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from noiseRemoval')
      this.$emit('emitted', ['deleteBlock', this])
    }
  }
}
</script>

<style>
div .noise-removal {
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
