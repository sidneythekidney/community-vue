<template>
    <AboutPage v-if="activePage === 'about'"/>
    <GroupsPage v-else-if="activePage === 'group'"/>
    <MapPage v-else/>
</template>

<script>
import AboutPage from './AboutPage.vue'
import GroupsPage from './GroupsPage.vue'
import MapPage from './MapPage.vue'
export default {
    components: {
        AboutPage,
        GroupsPage,
        MapPage,
    },
    props: {
        activePage: String
    }
}

</script>

<style>
</style>

