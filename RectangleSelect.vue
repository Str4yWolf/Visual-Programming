<template>
  <div id="outer-frame">
    <div id="image-frame">
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
      alert('Image area selected. Operations will be performed on them.')
    },
    cancel: function () {
      var div = document.getElementById('rectangle-select')
      div.border = '2px dotted black'
      div.hidden = 1
      alert('Operation cancelled.')
    }
  }
}
</script>

<style>
div #rectangle-select {
  border: 2px dotted black;
  position: absolute;
}
div #outer-frame {
  border: 2px solid black;
  position: absolute;
  height: 500px;
  width: 400px;
  background: #eeeeee;
}
div #image-frame {
  border: none;
  position: relative;
  height: 350px;
  width: 350px;
  top: 25px;
  left: 25px;
  background: white;
}
#btn1, #btn2 {
  position: relative;
  font-weight: bold;
  width: 150px;
  height: 75px;
  top: 40px;
  right: 25px;
  left: 25px;
  margin: 10px;
}
</style>
