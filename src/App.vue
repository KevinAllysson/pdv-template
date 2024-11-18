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
import Sidebar from './components/Sidebar.vue';

export default {
    components: {
        RouterLink,
        RouterView,
        Sidebar
    },
}

</script>
<style>
.main{
    height: 100vh;
    width: calc(100% - 250px); 
    overflow-y: auto;
    scroll-behavior: smooth;
    right: 0;
    position: absolute;
}
::-webkit-scrollbar-track {
    border-radius: 20px;
    margin-top: 25px;
}
::-webkit-scrollbar {
    width: 6px;
    border-radius: 20px;
    height: 7px !important;
}
::-webkit-scrollbar-thumb {
    background: #545454;
    border-radius: 20px;
}
</style>