<template>
    <div class="carrinho-page ">
        <div class="card-endereco">
            <span class=" text-2xl font-bold mb-4">Endereço de entrega</span>
            <div>
                <i class="pi pi-map-marker"></i>
                <span class="ml-2 font-bold text-sm">Rua Carlos Silveira, 218
                    Belo Jardim - PE</span>
            </div>
            <div class="mt-2">
                <i class="pi pi-clock"></i>
                <span class="ml-2 font-bold text-sm">20 min</span>
            </div>
        </div>
        <div class="grid grid-cols-2 items-center my-8 ">
            <div class="text-xl space-x-3">
                <i class="pi pi-cart-plus" style="font-size: 1.5rem;"></i>
                <span>Carrinho</span>
            </div>
            <span class="text-end">Pedido #19999</span>
        </div>
        <div class=" grid grid-cols-3 text-center border border-2-white rounded-full my-8">
            <div class="op-tipo" v-for="(item, index) in tipo" :key="index" :class="{ selected: item.isSelect }"
                @click="selectTipo(index)">
                {{ item.name }}
            </div>
        </div>
        <div class="rounded-xl bg-gradient-to-b from-[#343434] to-[#393939] p-4 text-white h-52 overflow-y-auto">
            <div class="grid grid-cols-4 item items-center" v-for="(pedido, index) in pedidos" :key="index">
                <img :src="pedido.strCategoryThumb" width="80" alt="prato" class="m-2">
                <div class="px-4 col-span-2">
                    <span class="text-md font-bold text-white">
                        {{ pedido.strCategory }}
                    </span>
                    <span class="text-xs italic block">
                        R$ 4,90
                    </span>
                    <div class="flex items-center">
                        <i class="pi pi-minus-circle cursor-pointer"
                            @click="pedido.count > 0 ? pedido.count-- : false;"></i>
                        <span class="m-2">{{ pedido.count }}</span>
                        <i class="pi pi-plus-circle cursor-pointer" @click="pedido.count++"></i>
                    </div>
                </div>
                <i class="pi pi-trash text-red-400 cursor-pointer" :style="{ fontSize: '1.5rem' }"
                    @click="pedidos.splice(index, 1)"></i>
            </div>
        </div>
        <div class="border-cut mt-20 mb-10"></div>
        <div class="codigo-promo ">
            <span>Código promocional</span>
            <div class="adicionar uppercase text-xs py-1 px-4">Adicionar</div>
        </div>
        <div class="py-2">
            <div class="mt-2"> 
                <span class="inline-block">Total</span>
                <span class="float-right">R$ 4,90</span>
            </div>
            <div class="mt-2"> 
                <span class="inline-block">Taxa de entrega</span>
                <span class="float-right">R$ 10,00</span>
            </div>
            <div class="border border-gray-400/50 my-2"></div>
            <div>
                <span class="inline-block font-bold">Total Geral</span>
                <span class="float-right font-bold">R$ 14,90</span>
            </div>
        </div>
        <div class="adicionar text-center py-2 my-1">
            Confirmar Pedido
        </div>
    </div>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            tipo: [
                { name: 'Entrega', isSelect: true },
                { name: 'No local', isSelect: false },
                { name: 'Pegue e leve', isSelect: false },
            ],
            pedidos: []
        }
    },
    created() {
        this.getCategorias()
    },
    methods: {
        selectTipo(selectedIndex) {
            this.tipo.forEach((item, index) => {
                item.isSelect = index === selectedIndex;
            });
        },
        async getCategorias() {
            try {
                const res = await axios.get('https://www.themealdb.com/api/json/v1/1/categories.php');
                console.log(res.data.categories);
                let count = 0;
                if (res.status == 200 || res.status == 204) {
                    for (const ctg of res.data.categories) {
                        if (count < 3) {
                            this.pedidos.push({
                                ...ctg,
                                count: 0
                            });
                            count++;
                        } else {
                            break;
                        }
                    }
                }
            } catch (err) {
                console.log('um erro ocorreu: ', err);
            }
        }
    }

}
</script>

<style>
.carrinho-page {
    --r: 35px;
    border-radius: 20px;
    background: #515151;
    mask: radial-gradient(var(--r) at 10% calc(70%), #0000 calc(100% - 1px), #000) calc(-1 * var(--r));
    margin: 40px 10px 40px 0;
    padding: 15px;
}

.card-endereco {
    border-radius: 20px;
    padding: 17px;
    background-color: #6D6D6D;
    display: flex;
    justify-content: start;
    flex-direction: column;
}

.selected {
    background: linear-gradient(180deg, rgba(232, 90, 82, 1) 0%, rgba(185, 51, 48, 1) 100%);
    border-radius: 9999px;
    font-weight: bold;
    color: white;
}

.op-tipo {
    padding: 7px;
    font-size: 12px;
    margin: 7px;
    cursor: pointer;
}

.item:not(:last-child) {
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    padding-bottom: 10px;
    margin-bottom: 10px;
}

.border-cut {
    border-top: 4px dashed #1D1D1D;
}

.codigo-promo {
    border-width: 2px;
    border-style: solid;
    padding: 5px 15px;

    border-top-color: #1d1d1d81;
    border-bottom-color: #fefefe25;
    border-left-color: #1d1d1d46;
    border-right-color: #1d1d1d46;
    border-radius: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.adicionar {
    background: linear-gradient(180deg, rgb(41, 41, 41) 0%, rgb(0, 0, 0) 100%);
    border-radius: 20px;
    font-weight: bold;
}
</style>
