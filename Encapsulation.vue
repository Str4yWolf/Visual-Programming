<template>
  <div class="encapsulation">
    <span style="text-align: center;">
      <span style=" padding: 0px 20px 0px 20px">
        <strong>Encapsulation</strong>
        <q-icon name="info" size="24px" color="yellow" title="Click for more information" style="padding: 10px;">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Encapsulation</q-card-title>
              <q-card-main>
                <p>
                  An encapsulation of the blocks you moved against the <strong>Encapsulator</strong>.
                   Enter a name in the text field to distinguish your encapsulations.
                   A <strong>Loop</strong> on this block will apply to all of the blocks it contains.
                  <br>
                  When you delete this block, all of the contained blocks will also disappear. If you have also
                   deleted the <strong>Starting Block</strong>, then hit <strong>Reset Blocks</strong> to get it back.
                </p>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </span>
    </span>
    <input id="encapsulation-id">
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
    }
  },
  methods: {
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from encapsulation')
      // this.$emit('emitted', ['deleteBlock', this])
      this.$root.$emit('deleteBlock', this)
    }
  }
}
</script>

<style>
div .encapsulation {
  height: 100px;
  width: 500px;
  padding: 20px;
  border: 4px solid blue;
  border-radius: 8px;
  background-color: goldenrod;
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
