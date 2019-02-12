<template>
  <div class="for-loop" id="for-loop">
    <div>
      <strong style="font-size: 80%;">Loop (Beta)</strong>
      <q-icon name="info" size="24px" color="amber" title="Click for more information">
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>For Loop (Beta)</q-card-title>
                  <q-card-main>
                    <p>Perform a chain of blocks as much as you enter into the input field. You can attach this block to the left of any type of normal block.
                     Currently, it works only on one block at a time
                     and the <strong>+/-</strong> buttons don't work yet. A workaround could be to <strong>encapsulate</strong> your chain of blocks and
                     attach this for loop to the encapsulation instead.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-icon>
    </div>
    For: <input id="forLoopNumber" style="width: 50px; padding-top: 7px; height: 25px;">
    <div style="padding: 5px;">
      <button class="for-loop-btn-add" @click="addUnit">+</button> &nbsp;
      <button class="for-loop-btn-subtract" @click="subtractUnit">-</button>
    </div>
    <div class="deletion">
    <button class="del-btn" @click="deleteBlock">x</button>
    </div>
  </div>
</template>

<script>
export default {
  // name: 'ForLoop',
  data () {
    return {
    }
  },
  methods: {
    /*
            Appends one unit (100px) below
    */
    addUnit: function () {
      var height = this.$el.style.height
      this.$el.style.height = (height + 100) + 'px'
    },
    /*
            Appends one unit (100px) below
    */
    subtractUnit: function () {
      var height = this.$el.style.height
      this.$el.style.height = (height - 100) + 'px'
    },
    /*
            calls the parent to delete this component
    */
    deleteBlock: function () {
      console.log('called deleteBlock from forLoop')
      this.$root.$emit('deleteBlock', this)
    }
  }
}
</script>

<style>
div .for-loop {
  height: 100px;
  width: 150px;
  padding: 10px;
  border: 4px solid #686cf5;
  background-color: #d3d4fa;
  border-radius: 8px;
}
.for-loop-btn-add {
  background-color: green;
  color: white;
  width: 50px;
}
.for-loop-btn-subtract {
  background-color: red;
  color: white;
  width: 50px;
}
button .del-btn {
/*  background: red;*/
}
</style>
