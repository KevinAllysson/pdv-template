<template>
    <div class="grid grid-cols-4 ">
        <div class="home-page col-span-3">
            <Categorias/>
            <Popular/>
            <Pedidos/>
        </div>
        <Carrinho />
    </div>
</template>
<script>
import Carrinho from '../Carrinho.vue';
import Categorias from './Categorias.vue';
import Popular from './Popular.vue';
import Pedidos from './Pedidos.vue';

export default {
    components: {
        Carrinho,
        Categorias,
        Popular,
        Pedidos
    }
}
</script>
<style >
    .home-page{
        width: 100%;
        height: 100vh;
        /* padding: 35px; */
    }
</style>