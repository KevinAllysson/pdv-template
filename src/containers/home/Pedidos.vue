<template >
    <div class="mt-10 px-9">
        <div class="flex flex-row justify-between ">
            <div>
                <span class="text-xl font-bold ">Relatórios de Pedidos</span>
             
            </div>
            <div class="flex flex-row items-center gap-2 cursor-pointer hover:underline">
                Ver mais
                <div class="rounded-md bg-gray-500 p-1 hover:bg-slate-500">
                    <i class="pi pi-angle-right "></i>
                </div>
            </div>
        </div>
        <div class="my-2">
            <div class="grid grid-cols-6 head-tbl">
                <div>Customer</div>
                <div>Order number</div>
                <div class="col-span-2">Address</div>
                <div>Amount</div>
                <div>Status</div>
            </div>
            <div class="grid grid-cols-6 tbody-tbl" v-for="pedido in pedidos">
                <div>{{ pedido.nome }}</div>
                <div>{{ pedido.numero }}</div>
                <div class="col-span-2">{{ pedido.endereco }}</div>
                <div>{{ pedido.valor }}</div>
                <div class="box-status" v-bind:class="pedido.status">{{ pedido.status }}</div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            pedidos: [
                {nome: 'Usuario 1', numero: '#558222659', endereco: 'Rua Afonso Pena, 249', valor: 200.48, status: 'entregue'},
                {nome: 'Usuario 2', numero: '#549564646', endereco: 'Rua Afonso Pena, 249', valor: 605.25, status: 'pendente'},
                {nome: 'Usuario 3', numero: '#545515987', endereco: 'Rua Afonso Pena, 249', valor: 163.16, status: 'cancelado'},
                
            ]
        }
    },
}
</script>
<style >
    .head-tbl{
        padding: 6px 16px;
        background-color: #424242;
        border-radius: 50px;
    }
    .tbody-tbl{
        margin: 14px 16px;
    }
    .box-status{
        background-color: #424242;
        border-radius: 50px;
        padding: 4px 10px;
        width: 100px;
        text-align: center;
        text-transform: capitalize;
    }
    .entregue{
        color: #27fe68;
        background-color: #21462c;
    }
    .pendente{
        color: #FCB80B;
        background-color: #3e4621;
    }
    .cancelado{
        color: #FA0000;
        background-color: #462121;
    }
</style>