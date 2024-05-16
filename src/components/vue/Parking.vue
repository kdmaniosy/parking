<script setup>
import { ref } from 'vue';

const contador = ref(0);


const buttons = ref([
    { id:1, text: "Libre", color: "bg-green-600" },
    { id:2, text: "Libre", color: "bg-green-600" },
    { id:3, text: "Libre", color: "bg-green-600" },
    { id:4, text: "Libre", color: "bg-green-600" },
    { id:5, text: "Libre", color: "bg-green-600" },
    { id:6, text: "Libre", color: "bg-green-600" }
]);

const buttons2 = ref([
    { id:1, text: "Libre", color: "bg-green-600" },
    { id:2, text: "Libre", color: "bg-green-600" },
    { id:3, text: "Libre", color: "bg-green-600" }
])

function toggleButton(buttonId) {
    const button = buttons.value.find(b => b.id === buttonId);
    if(button.text === "Libre"){
        button.text = "Ocupado";
        button.color = "bg-red-400";
        contador.value += 2000;
    }else{
        button.text = "Libre";
        button.color = "bg-green-600";
    }
}
function toggleButton2(buttonId){
    const button = buttons2.value.find(b => b.id === buttonId);
    if(button.text === "Libre"){
        button.text = "Ocupado";
        button.color = "bg-red-400";
        contador.value += 1500;
    }else{
        button.text = "Libre";
        button.color = "bg-green-600"
    }
}

function reset(){
    contador.value = 0;
    buttons.value.forEach(button => {
        button.text = "Libre";
        button.color = "bg-green-600";
    });
    buttons2.value.forEach(button => {
        button.text = "Libre";
        button.color = "bg-green-600"
    });
}


</script>

<template>
    <div class="bg-slate-300 container mx-auto p-4">
        <h1 class="text-3xl font-bold mb-6">Parqueadero</h1>
        <div class="mb-8">
            <h2 class="text-2xl font-semibold mt-8">Sección de carros</h2>
            <div class="grid grid-cols-3 gap-4 mt-6 grid-rows-2">
                <button class="py-7 w-24 text-white rounded" v-for="button in buttons" :key="button.id"
                :class="button.color" @click="toggleButton(button.id)">
                    {{ button.text }}
                </button>
            </div>
            <div class="mt-10">
                <h2 class="text-2xl font-semibold">Sección de motos</h2>
                <div class="grid grid-cols-3 gap-4">
                    <button class="py-7 w-24 text-white rounded" v-for="button in buttons2" :key="button.id"
                    :class="button.color" @click="toggleButton2(button.id)">
                    {{ button.text }}
                </button>

                </div>
            </div>
            <div class="mt-10">
                <h2 class="font-semibold text-xl">Total a pagar</h2>
                <h2 class="text-blue-500 font-bold text-xl">Total:
                    {{ contador }}
                </h2>
                <button class="bg-yellow-500 py-3 px-5 mt-4"
                @click="reset"
                >Reiniciar total</button>
            </div>
        </div>
    </div>
</template>


