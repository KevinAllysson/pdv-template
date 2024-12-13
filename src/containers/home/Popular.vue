<template>
    <div>
        <div class="flex flex-row justify-between px-9">
            <div>
                <span class="text-xl font-bold ">Refeições Populares</span>
                <div class="text-gray-300 italic"><span class="color-active">20+ novos</span> pratos foram
                    adicionadas essa semana</div>
            </div>
            <div class="flex flex-row items-center gap-2 cursor-pointer hover:underline">
                Ver mais
                <div class="rounded-md bg-gray-500 p-1 hover:bg-slate-500">
                    <i class="pi pi-angle-right "></i>
                </div>
            </div>
        </div>
        <div class="flex flex-row relative mt-4 pl-9 ">
            <div class="flex flex-row overflow-x-auto gap-6 pb-1 pr-24">
                <div v-for="(cat, index) in categorias" :key="cat.idCategory" :title="cat.strCategory"
                    class="relative flex items-center flex-col ">
                    <img :src="cat.strCategoryThumb" class="h-24 absolute transform z-10  ">
                    <div class="box mt-12 text-white">
                        <div class="mt-12 flex flex-col">
                            <div class=" text-center p-2 pt-4 font-bold text-lg">Hamburger</div>
                            <div class="text-center">
                                <span class="text-sm text-gray-500">A partir</span>
                                <div class="font-bold text-xl">R$ 25,00</div>
                            </div>
                            <div class="flex justify-between items-center px-2">
                                <div>
                                    <i class="pi pi-star-fill" style="color: orange;"></i>
                                    <span class="font-bold pl-1">4.5</span>
                                </div>
                                <div class="flex flex-col text-end">
                                    <span class="text-gray-500 text-sm">1360</span>
                                    <span class="font-bold text-base">Vendidos</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="sombra "></div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            categorias: []
        }
    },
    created() {
        this.getCategorias()
    },
    methods: {
        async getCategorias() {
            try {
                const res = await axios.get('https://www.themealdb.com/api/json/v1/1/categories.php');
                let count = 0;
                if (res.status == 200 || res.status == 204) {
                    for (const ctg of res.data.categories) {
                        if (count < 6) {
                            this.categorias.push(ctg);
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