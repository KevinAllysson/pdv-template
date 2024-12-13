<template>
    <div id="app">
        <Sidebar/>
        <div class="main">
            <router-view/>
        </div>
    </div>
</template>
<script>
import { RouterLink, RouterView } from 'vue-router';
import Sidebar from './components/layout/Sidebar.vue';

export default {
    components: {
        RouterLink,
        RouterView,
        Sidebar
    },
}

</script>