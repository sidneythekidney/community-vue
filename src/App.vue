<template>
  <div class="full-page">
    <div class="navbar">
      <TopNavBar 
      v-bind:activePage="this.activePage"
      @changeTab="this.activePage=$event"
      />
    </div>
    <div class="main-content">
      <MainPage v-bind:activePage="this.activePage"/>
    </div>
  </div>
</template>

<script>
import TopNavBar from './components/TopNavBar.vue'
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  data: function() {
    return {
      activePage: 'map'
    }
  },
  components: {
    TopNavBar,
    MainPage,
  },
}
</script>

<style>
body {
  margin: 0px;
}
.full-page {
  display: flex;
  flex-flow: column;
  min-height: 100vh;
  min-width: 100vw;
  width: 100%;
  margin: 0px;
}
.navbar {
  flex-grow: 0;
  height: 75px;
}
.main-content {
  flex-grow: 1;
}
</style>
