<template>
  <div class="rectangle-select-outer">
    <div style="padding: 15px 0px 0px 30px; font-weight: bold;">
      Select Region
      <q-icon name="info" size="24px" color="amber" title="Click for more information"
        style="display: inline; padding: 0px 0px 0px 30px;">
        <q-popover>
          <q-card inline style="width: 500px">
            <q-card-title>Select Region</q-card-title>
            <q-card-main>
              <p>Dockable to: Image Preview</p>
              <p>Select a region of interest on which actions will be performed
                  Press <strong>Select</strong> to confirm, or <strong>Cancel</strong> to revert to original image.
              </p>
            </q-card-main>
          </q-card>
        </q-popover>
      </q-icon>
    </div>
    <div class="rectangle-select-image">
      <img src="../statics/dummy.jpg" class="responsive">
      <div id="rectangle-select"
        @mousedown.native="selectStart($event,1)"
        @mouseup.native="selectEnd($event,1)"
        @mousemove.native="selectActive($event,1)" hidden>
      </div>
    </div>
    <button id="btn1" @click="select()">Select</button>
    <button id="btn2" @click="cancel()">Cancel</button>
  </div>
</template>

<script>
export default {
  // name: '',
  data () {
    return {
      blocktype: 'RectangleSelect',
      // What data can be input
      intype: 'image',
      // What data can be output
      outtype: 'image',
      x1: 0,
      y1: 0,
      x2: 0,
      y2: 0
    }
  },
  methods: {
    restyle: function () {
      console.log('RectangleSelect restyle')
      var div = document.getElementById('rectangle-select')
      var x3 = Math.min(this.x1, this.x2) // Smaller X
      var x4 = Math.max(this.x1, this.x2) // Larger X
      var y3 = Math.min(this.y1, this.y2) // Smaller Y
      var y4 = Math.max(this.y1, this.y2) // Larger Y
      div.style.left = x3 + 'px'
      div.style.top = y3 + 'px'
      div.style.width = x4 - x3 + 'px'
      div.style.height = y4 - y3 + 'px'
    },
    selectStart: function (event) {
      console.log('RectangleSelect')
      var div = document.getElementById('rectangle-select')
      div.hidden = 0 // Unhide the div
      this.x1 = event.clientX // Set the initial X
      this.y1 = event.clientY // Set the initial Y
      this.restyle()
    },
    selectActive: function (event) {
      this.x2 = event.clientX // Update the current position X
      this.y2 = event.clientY // Update the current position Y
      this.restyle()
    },
    selectEnd: function () {
      var div = document.getElementById('rectangle-select')
      div.hidden = 1 // Hide the div
    },
    select: function () {
      var div = document.getElementById('rectangle-select')
      div.border = '2px solid red'
      this.$root.$emit('notify', 'Image region selected. Program will be performed on it.', 'positive')
    },
    cancel: function () {
      var div = document.getElementById('rectangle-select')
      div.border = '2px dotted black'
      div.hidden = 1
      this.$root.$emit('notify', 'Selection cancelled.', 'negative')
    }
  }
}
</script>

<style>
div #rectangle-select {
  border: 2px dotted black;
  position: absolute;
}
div .rectangle-select-outer {
  border: 2px solid black;
  height: 450px;
  width: 400px;
  background: #fae5d3;
}
div .rectangle-select-image {
  border: none;
  position: relative;
  max-height: 400px;
  max-width: 350px;
  top: 25px;
  left: 25px;
  background: white;
  overflow: hidden;
}
#btn1, #btn2 {
  position: relative;
  font-weight: bold;
  width: 155px;
  height: 50px;
  top: 30px;
  right: 25px;
  left: 25px;
  margin: 10px;
}
</style>
