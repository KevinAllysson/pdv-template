<template>
    <div class="sidebar">
        <div class="flex justify-center">
            <img src="../../assets/images/logo.png" alt="logo" class="brand-logo">
        </div>
        <div class="flex flex-row ">
            <div class="icon-bar"></div>
            <div class="menu">
                <div v-for="(item, index) in menu" :key="index" class="my-4">
                    <div class="grid grid-cols-3 items-center color-text-menu" :class="{ 'color-active ': item.isSelect }"
                        @click="menu.forEach((element) => { element.isSelect = false }); item.isSelect = true">

                        <i :class="[{ 'color-active ': item.isSelect }, item.icone]" style="font-size: 1.2rem;" class="mx-6 "></i>
                        <div class="mx-2 text-menu">{{ item.nome }}</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="flex items-start justify-center  ">
            <div class="fixed mb-10 flex justify-between bottom-0 menu-footer">
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
            ],
            
        }
    },
}
</script>