<template>
    <div class="container">
        <div id="community-header" class="main-title">
            <h1 class="title-text"
            v-on:click="setActiveTab('map')">Community</h1>
        </div>
        <div id="map-header" class="title">
            <h3 class="title-text"
                v-bind:class="{'highlight-title': this.activePage === 'map'}"
                v-on:click="setActiveTab('map')">Map</h3>
        </div>
        <div id="groups-header" class="title">
            <h3 class="title-text"
                v-bind:class="{'highlight-title': this.activePage === 'group'}"
                v-on:click="setActiveTab('group')">Groups</h3>
        </div>
        <div id="about-header" class="title">
            <h3 class="title-text"
                v-bind:class="{'highlight-title': this.activePage === 'about'}"
                v-on:click="setActiveTab('about')">About</h3>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        activePage: String
    },
    methods: {
        setActiveTab: function (tab) {
            this.$emit('changeTab', tab);
        }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap');
.container {
    position: absolute;
    width: 100%;
    height: 75px;
    top:0px;
    left: 0px;
    background-color: black;
    color: white;
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: flex-start;
    vertical-align: middle;
    cursor: pointer;
}
.main-title{
    color: #ebe6d8;
    margin-right: 30px;
    margin-left: 10px;
    font-size: 15px;
}
.title {
    color: #ebe6d8;
    margin-right: 10px;
    margin-top: 15px;
    font-size: 15px;
}
.main-title:hover, .title:hover {
    color: #345eeb;
}
.main-title:active, .title:active {
    color: #38b8eb;
}
.title-text {
    font-family: 'Open Sans', sans-serif;
}
.highlight-title {
    color: #38b8eb;
}
</style>