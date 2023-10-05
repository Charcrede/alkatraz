<script>
export default {
    data(){
        return {
            acces : false,
            quiz : false,
            stats : false,
            editor : false,
        }
    },
    methods:{
        activate(){
            this.active= true;
        },
    }
}
</script>
<template>
    <header>
        <div>LOGO</div>
        <ul>
            <li>
                <a @click="$emit('switch-quiz'), quiz = true" :class="{act: quiz}">Quiz</a>
            </li>
            <li>
                <a>Stats</a>
            </li>
            <li>
                <a @click="$emit('switch-editors'), editor = true" :class="{ act: editor }">Editeurs de quiz</a>
            </li>
            <li>
                <a @click="$emit('switch-acces'), acces = true" :class="{ act: acces }">Accès</a>
            </li>
        </ul>
    </header>
</template>
<style>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 10%;
    }
    header ul{
        display: flex;
        justify-content: space-evenly;
        gap: 1rem;
        list-style: none;
    }
    ul a{
        display: block;
        text-decoration: none;
        background-color: #e7f3fe;
        padding: .2rem .5rem;
        border-radius: 10px;
        color:#00bd7e;
        border:2px solid #e7f3fe;
        transition: 1s;
    }
    ul a:hover, .act{ 
        background-color: #00bd7e;
        color: #e7f3fe;
        cursor:pointer;
    }
</style>