<template>
    <button id="newEventButton" v-if="!formDisplayed" v-on:click="openForm()"> 
      <span id="newEventPlus">&#43;</span>
      New Event
    </button>
    <NewEventForm v-if="formDisplayed" @closeForm="this.formDisplayed=false"/>
    <div id="mapContainer"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
import NewEventForm from './NewEventForm.vue';

export default {
  data() {
    return {
      map: null,
      formDisplayed: false
    };
  },
  mounted() {
    this.map = L.map("mapContainer").setView([42.4606, -83.1346], 12);
    L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(this.map);    
  },
  onBeforeUnmount() {
    if (this.map) {
      this.map.remove();
    }
  },
  methods: {
    openForm: function() {
      this.formDisplayed = true;
    }
  },
  components: {
    NewEventForm
  }
};
</script>

<style scoped>
#mapContainer {
  position: absolute;
  top: 75px;
  bottom: 0;
  width: 100%;
  z-index: 10;
}
#newEventButton {
  position: absolute;
  top: 100px;
  left: 45%;
  z-index: 11;
  width: 130px;
  height: 45px;
  background-color: black;
  color: #ebe6d8;
  border-radius: 4px;
  font-size: 18px;
}
#newEventButton:hover {
  background-color: #38b8eb;
  color: black;
}
#newEventPlus {
  font-size: 18px;
}
</style>