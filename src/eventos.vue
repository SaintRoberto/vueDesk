<script setup>
import { ref, computed } from 'vue'

const styleColor = 'color: red';
const styleColor2 = 'color: green';

const vueDinamic = 'Vue dinamico';
let counter = ref(0);
const listaNumero = ref([1, 2, 4]);
const estadoBtn = ref(false);

const incremente = () => {
    counter.value++;
    console.log(counter);
}

const decremente = () => {
    counter.value--;
    console.log(counter);
}

const reset = () => {
    counter.value = 0;
    console.log(counter);
}

const classCount = computed(() => {
    if (counter.value == 0) {
        return 'reset';
    } else if (counter.value > 0) {
        return 'increment';
    } else {
        return 'decrement';
    }
});

const agregarNum = (counter) => {

    if (!listaNumero.value.includes(counter)) {
        listaNumero.value.push(counter);
    } 
}

const validar = computed(() => {
    if (!listaNumero.value.includes(counter.value)) {
        return false;
    } else {
        return true;
    }
});

</script>


<template>
    <ul>
        <li v-for=" (num, index) in listaNumero" :key="index">
            {{ num }}
        </li>
    </ul>

    <label :class="classCount">{{ counter }}</label><br>
    <button v-on:click="incremente">+</button>

    <button v-on:click="decremente">-</button>
    <button v-on:click="reset">reset</button>
    <button v-on:click="agregarNum(counter)" :disabled="validar">
        Add
    </button>

</template>

<style>
.increment {
    color: green;
}

.decrement {
    color: red;
}

.reset {
    color: yellow;
}
</style>