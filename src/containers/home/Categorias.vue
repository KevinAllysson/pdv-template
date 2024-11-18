<template>
    <div class="p-9">
        <div class="flex flex-row justify-between">
            <div>
                <span class="text-xl font-bold ">Categorias</span>
                <div class="text-gray-300 italic"><span class="color-active">10+ novas</span> Categorias adicionadas
                    essa semana</div>
            </div>
            <div class="flex flex-row  items-center gap-2 cursor-pointer hover:underline">
                Ver mais
                <div class="rounded-md bg-gray-500 p-1 hover:bg-slate-500">
                    <i class="pi pi-angle-right "></i>
                </div>
            </div>
        </div>
        <div class="mt-4">
            <div class=" flex flex-row justify-around overflow-x-auto">
                <div v-for="(cat, index) in categorias" :key="cat.idCategory" class="sty-categ rounded-full h-32 w-32 " :title="cat.strCategory">
                    <img :src="cat.strCategoryThumb" alt="" srcset="" class="">
                </div>
            </div>
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
                        if (count < 7) {
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
<style>
.sty-categ {
    display: flex;
    align-items: center;
    background: linear-gradient(135deg, rgba(126,117,100,1) 0%, rgba(97,77,58,1) 100%);
}
</style>