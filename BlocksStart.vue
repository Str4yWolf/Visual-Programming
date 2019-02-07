<!-- TODO:
  fix interblock reference error: every block reads from
  one single input field only (wrong get element by Id)
-->
<template>
  <div class="blocks-start">
    <span style="text-align: center; font-weight: bold;"><span style="background-color: powderblue; padding: 0px 40px 0px 40px;">STARTING BLOCK</span> (Load Image from Files)</span>
    <q-uploader url="" />
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
  }
}
</script>

<style>
div .blocks-start {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid black;
  border-radius: 8px;
  background-color: #e6d4f9;
}
</style>
