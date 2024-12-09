<script setup> 
    import { reactive, computed } from 'vue';

    const estado = reactive({
        num1: 0,
        num2: 0,
        operador: ''
    })

    function alteraNum1(evento){
        estado.num1 = parseFloat(evento.target.value);
    }
    function alteraNum2(evento){
        estado.num2 = parseFloat(evento.target.value);
    }

    const result = computed(() => {
        switch (estado.operador) {
            case 'add':
                return estado.num1 + estado.num2;
            case 'subtract':
                return estado.num1 - estado.num2;
            case 'multiply':
                return estado.num1 * estado.num2;
            case 'divide':
                return estado.num2 !== 0 ? estado.num1 / estado.num2 : 'Erro: divisão por zero';
            default:
                return 0;
        }
    });

</script>

<template>
    <div class="container calculator bg-secondary mt-3">
        <h1 class="text-center">Calculadora Aritmética</h1>
        <div class="input-container">
            <input class="col-5 text-center" type="number" v-model.number="estado.num1" @input="alteraNum1" placeholder="Digite o primeiro número" />
            <select class="col-2 text-center" v-model="estado.operador">
                <option value="add">+</option>
                <option value="subtract">-</option>
                <option value="multiply">X</option>
                <option value="divide">÷</option>
            </select>
            <input @input="alteraNum2" class="col-5 text-center" type="number" v-model.number="estado.num2" placeholder="Digite o segundo número" />
        </div>
        <p class="result text-center fs-1">Resultado: {{ result }}</p>
    </div>
</template>

<style scoped>

</style>
