<template>
  <div ref="draggableContainer" id="draggable-container">
    <div id="draggable-header" @mousedown="dragMouseDown">
        <h3 id="dragMessage">Click here to drag!</h3>
    </div>
    <button id="closeFormButton" v-on:click="closeForm()">X</button>
    <input type="text">
  </div>
</template>

<script>
export default {
  name: 'DraggableDiv',
  data: function () {
    return {
      positions: {
        clientX: undefined,
        clientY: undefined,
        movementX: 0,
        movementY: 0
      }
    }
  },
  methods: {
    dragMouseDown: function (event) {
      event.preventDefault()
      // get the mouse cursor position at startup:
      this.positions.clientX = event.clientX
      this.positions.clientY = event.clientY
      document.onmousemove = this.elementDrag
      document.onmouseup = this.closeDragElement
    },
    elementDrag: function (event) {
      event.preventDefault()
      this.positions.movementX = this.positions.clientX - event.clientX
      this.positions.movementY = this.positions.clientY - event.clientY
      this.positions.clientX = event.clientX
      this.positions.clientY = event.clientY
      // set the element's new position:
      this.$refs.draggableContainer.style.top = (this.$refs.draggableContainer.offsetTop - this.positions.movementY) + 'px'
      this.$refs.draggableContainer.style.left = (this.$refs.draggableContainer.offsetLeft - this.positions.movementX) + 'px'
    },
    closeDragElement () {
      document.onmouseup = null
      document.onmousemove = null
    },
    closeForm: function() {
        this.$emit('closeForm');
    }
  }
}
</script>

<style>
#draggable-container {
  position: absolute;
  left: 200px;;
  top: 100px;
  height: 400px;
  width: 300px;
  border-style: solid;
  border-color: black;
  border: 0px;
  background-color: #ebe6d8;
  z-index: 110;
}
#draggable-header {
  position: relative;
  z-index: 120;
  height: 30px;
  margin: 0px;
  background-color: black;
  color: #ebe6d8;
  text-align: center;
}
#draggable-header:hover {
  background-color: #38b8eb;
  color: black;
}
#closeFormButton {
  position: absolute;
  margin: 0px;
  right: 3px;
  top: 33px;
  background-color: black;
  color: #ebe6d8;
  border-radius: 4px;
  font-size: 18px;
}
#closeFormButton:hover {
  background-color: #38b8eb;
  color: black;
}
#dragMessage {
  margin: 0px;
}

</style>