<template>
    <h2>{{ customTitle }}</h2>
    <p> {{ counter }} <sup>2</sup> = {{  squareCounter }}</p>

    <div>
       <!--  <button @click="counter++">+1</button>
        <button @click="counter--">-1</button> -->
        <button v-on:click="increment">+1</button>
        <button v-on:click="decrement">-1</button>
    </div>


</template>

<script>
export default {
    props: {
        title: String,
        start: {
            type: Number,
            default: 100,
            required: true,
            validator( value ){
                return value >= 0;
            }
        }
    },
    name: 'counterComponent',

    data() {
        return {
             counter: this.start
        };
    },

    mounted() {
        
    },
    //se ejecutan las N veces que se llame
    methods: {
        getSquareValue(){
             return this.counter * this.counter;
        },
        increment(){
            this.counter++;
        },
        decrement(){
            this.counter--;
        }
    },
    //propiedades computadas "valores que se calculan en tiempo real" y no se mandan a llamar como metodos !()
    computed:{ //se guardan en el cache, ayuda a que los procesos sean mas eficientes
        squareCounter(){ //se ejecuta solo cuando cambia el valor de counter
            return this.counter * this.counter;
        },
        customTitle(){
            return this.title ?? 'Counter';
        }
    }
};
</script>

<style>
    button{
        background-color: #64bb87;
        border-radius: 5px;
        color: #fff;
        cursor: pointer;
        margin: 0 10px;
        padding: 10px;
    }

    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out
    }
</style>