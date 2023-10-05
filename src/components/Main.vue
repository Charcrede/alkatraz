<script setup>
defineEmits(['update:modelValue'])
</script>
<script>
export default {
    data() {
        return {
            min: "",
            i: 0,
            int: 0,
            quizzes: [],
            quizz: "",
            ans: '',
            quiz: true,
            nbrAnser: '',
            nbrAnsers: true,
            //    pushedAnsers: '',
            g: 0,

        }
    },
    methods: {
        addQuiz() {
            if (this.quizz !== "") {
                this.quizzes.push({ question: this.quizz, reponses: [] });
                this.quizz = "";
                this.quiz = false;
                console.log(this.quizzes);
            }
        },
        addNbrAnsers() {
            if (Number(this.nbrAnser)) {
                this.int = Number(this.nbrAnser);
                this.nbrAnser = "";
                this.nbrAnsers = false;
            };
        },
        addAnsers() {
            if (this.i < this.int) {
                this.quizzes[this.g].reponses.push(this.ans);
                this.ans = "";
                this.i++;
                console.log(this.quizzes);
            }
            if (this.i === (this.int)) {
                this.i = 0;
                this.int = 0;
                this.nbrAnsers = true;
                this.quiz = true;
                this.g++
            };
        },
    }
}
</script>
<template>
    <form @submit.prevent>
        <fieldset>
            <legend>Editeur de Quiz</legend>
            <div class="parentDesInputs">
                <div class="lesInput input" v-if="quiz"><label for="">Question ? </label><input type="text"
                        placeholder="veuillez entrer la question" v-model="quizz" @keydown.enter="addQuiz">
                </div>

                <div class="lesInput input" v-if="nbrAnsers"><label for="">Réponse possible ? </label><input type="text"
                        id="iteration" v-model="nbrAnser" @keydown.enter="addNbrAnsers"></div>

                <div class="lesInput input"><label for="">Diverses réponses :</label><input type="text"
                        placeholder="veuillez entrer les réponses possible" id="answer" v-model="ans"
                        @keydown.enter="addAnsers"></div>

            </div>
            <div class="button">
                <button>editer un Quiz</button>
            </div>

        </fieldset>
        <fieldset>
            <legend>Durée du quiz</legend>
            <div class="parentDesInputs">
                <div><input @keydown.enter="$emit('update:modelValue', $event.target.value)" placeholder="entrer un nombre et entrez"/></div>
            </div>
            <div class="button">
            </div>

        </fieldset>
    </form>
    <div id="div" v-for="(quiz, u) of quizzes" :key="u">
        <p>
            {{ quizzes[u].question }}
        </p>
        <ul>
            <li v-for="(anser, i) of quizzes[u].reponses" :key="i"><input type="radio" :name="u">
                {{ quizzes[u].reponses[i] }}</li>
        </ul>
    </div>j
</template>
<style>
form {
    max-width: 700px;
    margin-inline: auto;
}

form fieldset {
    border-radius: 20px;
}

legend {
    padding: .4rem;
}

.input {
    margin: 1rem;
}

.input input {
    border-radius: 10px;
    float: right;
    margin-right: 50px;
    padding: .3rem;
}

.button {
    display: flex;
    justify-content: center;
}

.button a,
.button button {
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 10px;
    background-color: dodgerblue;
    color: #fff;
    text-decoration: none;
}

input[type="radio"] {
    display: inline-block;
    height: 20px;
    width: 20px;
}

ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

.div {
    max-width: 700px;
    margin-inline: auto;
}
</style>