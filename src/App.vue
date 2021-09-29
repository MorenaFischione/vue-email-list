<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div v-if=" listaEmail.lenght = 10 ">
      <ul>
        <li v-for="(email, element) in listaEmail" :key="element">{{ email }}</li>
      </ul>
    </div>
   
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import axios from "axios";

export default {
  name: 'App',

  components: {
    HelloWorld
  },
  data: function () {
    return {
      emailCasuale : '',
      listaEmail: [],
    }
  },

  mounted(){
    console.log(axios);
    let self = this;

    for (let i=0; i<10; i++){
      axios.get("https://flynn.boolean.careers/exercises/api/random/mail")
      .then(function (response) {
        const result = response.data; 
        console.log(result.response);
        self.emailCasuale = result.response;
        self.listaEmail.push(self.emailCasuale);
        console.log(self.listaEmail);

      });
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
