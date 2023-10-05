<style>
.chrono {
    background-color: #fff;
    color: black;
    display: inline-block;
    margin: 0 auto;
    padding: 1rem;
    border: 5px solid #00bd7e;
    font-size: 1rem;
}
</style>
<template>
    <p @click="timer()" class="chrono"> {{ chrono.min }} : {{ chrono.secondes }} : {{ chrono.cent }}</p>
    <div id="div" v-for="(quiz, u) of quizzes" :key="u">
        <p>
            {{ quizzes[u].question }}
        </p>
        <ul>
            <li v-for="(anser, i) of quizzes[u].reponses" :key="i"><input type="radio" :name="u">
                {{ quizzes[u].reponses[i] }}</li>
        </ul>
        <button> Soumettre</button>
    </div>
</template>
<script setup>
import { reactive } from 'vue';

const props = defineProps(['title']);
let min = 25;
let chr = "";
console.log(min);
let chrono = reactive({
    cent: 99,
    secondes: 59,
    min : 20,
    intervalId: "",
});
function timer() {
    // console.log(min);
    if (chrono.min > -1) {
        chrono.intervalId = setInterval(() => {
            chrono.cent--;
            if (chrono.cent === 0) {
                chrono.cent = 100;
                chrono.secondes--;
            }
            else if (chrono.secondes === 0) {
                chrono.secondes = 60;
                chrono.min--;
            }
        }, 10);
        chr = `${chrono.min - 1} : ${chrono.secondes} : ${chrono.cent}`
    }
    else if (chrono.min <= -1) {
        clearTimeout(chrono.intervalId);
        chr =  `00 : 00 : 00`
    }
}
// console.log(timer());
</script>
<script>
export default {
    data() {
        return {
            chron: true,
        }
    },
    methods: {

    }
}
</script>