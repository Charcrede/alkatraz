<script>
export default {

    data() {
        return {
            links : [
                {lien : "https://inertiajs.com/", name : "inertiajs"},
                {lien : "https://vuejs.org/", name : "vuejs"},
                {lien : "https://router.vuejs.org/", name : "router.vuejs"},
                {lien : "https://pinia.vuejs.org/", name : "pinia.vuejs"},
                {lien : "https://vuex.vuejs.org/", name : "vuex.vuejs"},
                {lien : "https://nuxtjs.org/", name : "nuxtjs"},
                {lien : "https://nuxt.com/", name : "nuxt"},
                {lien : "https://vue-native.io/", name : "vue-nativ"},
                {lien : "https://vee-validate.logaretm.com/v4/", name : "vee-validate.logaretm"},
                {lien : "https://reactjs.org/", name : "reactjs"},
                {lien : "https://reactrouter.com/", name : "reactrouter"},
                {lien : "https://nextjs.org/", name : "nextjs"},
                {lien : "https://reactnative.dev/", name : "reactnative"},
                {lien : "https://remix.run/", name : "remix"},
                {lien : "https://angular.io/", name : "angula"},
                {lien : "https://spring.io/", name : "sprin"},
                {lien : "https://flutter.dev/", name : "flutter"},
                {lien : "https://axios-http.com/docs/intro", name : "axios"},
                {lien : "https://www.cypress.io/", name : "cypres"},
                {lien : "https://vitest.dev/", name : "vitest"},
                {lien : "https://vitejs.dev/", name : "vitejs"},
                {lien : "https://www.typescriptlang.org/", name : "typescriptlang"},
                {lien : "https://webpack.js.org/", name : "webpack.js"},
                {lien : "https://firebase.google.com/", name : "firebase.google"},
                {lien : "https://www.mongodb.com/", name : "mongodb"},
                {lien : "https://tailwindcss.com/", name : "tailwindcss"},
                {lien : "https://sass-lang.com/", name : "sass-lang"},
                {lien : "https://nodejs.org/en/", name : "nodejs.or"},
                {lien : "https://www.python.org/", name : "python"},
                {lien : "https://www.djangoproject.com/", name : "djangoprojec"}
            ], 
            nom :"",
            address : "",
        }
    },
    methods:{
        adding(){
            this.links.push({lien : this.address, name : this.nom});
        }
    }
}

</script>
<template>
    <ul class="acces">
        Vos accès internet
        <li v-for="(link, i) of links" :key="i"><a :href="link.lien" target="_blank"> {{ link.name }}</a></li>
    </ul>
    <form @submit.prevent v-if="admin">
    <fieldset>
      <legend>Ajoutez un nouveau lien</legend>
      <div class="parentDesInputs">
        <div class="lesInput input"><label for="">Nom :</label><input type="text" placeholder="veuillez le nom du lien"
            v-model="nom">
        </div>

        <div class="lesInput input"><label for="">Address :</label><input type="text" v-model="address"
            placeholder="ex : https://www.python.org/"></div>
      </div>
      <div class="button">
        <button @click.prevent="adding()">Ajoutez un lien</button>
      </div>

    </fieldset>
  </form>
</template>
<style>
.acces{
    text-align: center;
}
.acces a{
    width: 50%;
    margin-inline: auto;
    padding: .5rem;
    margin-block: 1rem;
}
</style>