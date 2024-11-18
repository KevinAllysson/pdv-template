<template>
    <div class="sidebar ">
        <div class="flex justify-center">
            <img src="../assets/logo.png" alt="logo" width="150px">
        </div>
        <div class="flex flex-row ">
            <div class="barra-icones"></div>
            <div class="menu-info">
                <div v-for="(item, index) in menu" :key="index" class="my-4">
                    <div class="grid grid-cols-3 items-center color-text" :class="{ 'color-active ': item.isSelect }"
                        @click="menu.forEach((element) => { element.isSelect = false }); item.isSelect = true">

                        <i :class="[{ 'color-active ': item.isSelect }, item.icone]" style="font-size: 1.2rem;" class="mx-6 "></i>
                        <div class="mx-2 ">{{ item.nome }}</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="flex items-start justify-center  ">
            <div class="fixed mb-10 flex justify-between bottom-0">
                <div class="circle-icons">
                    <i class="pi pi-cog"></i>
                </div>
                <div class="circle-icons">
                    <i class="pi pi-bell mx-4"></i>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            menu: [
                { nome: 'Dashboard', icone: 'pi pi-objects-column', isSelect: true },
                { nome: 'Pedidos', icone: 'pi pi-list', isSelect: false },
                { nome: 'Financeiro', icone: 'pi pi-credit-card', isSelect: false },
                { nome: 'Logout', icone: 'pi pi-sign-out', isSelect: false },
            ]
        }
    },
}
</script>
<style>
.sidebar {
    background: rgb(29, 29, 29);
    background: linear-gradient(0deg, rgba(29, 29, 29, 1) 0%, rgba(33, 33, 33, 1) 30%, rgba(44, 44, 44, 1) 70%, rgba(48, 48, 48, 1) 100%);
    width: 250px;
    position: fixed;
    height: 100vh;
}

.barra-icones {
    width: 70px;
    background-color: #545454;
    height: 60vh;
    --r: 30px;

    border-block: var(--r) solid #00000000;
    border-radius: 0 var(--r) var(--r) 0/calc(2*var(--r));
    mask:
        radial-gradient(var(--r) at 100% var(--r), #0000 98%, #000000 101%) 0 calc(-1*var(--r))/var(--r) 100% repeat-y,
        conic-gradient(#000 0 0) padding-box;
}

.menu-info {
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: absolute;
    left: 0;
    height: 60vh;
    width: 100%;
}

.circle-icons {
    width: 40px;
    height: 40px;
    background-color: #5E3A38;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 10px;
}

.color-text {
    color: #e3e3e4;
}

.color-text:hover {
    color: #ED5D55;
    cursor: pointer;
}

.color-active {
    color: #ED5D55;
}
</style>