<template>
  <div id="app">
    <h1>在线翻译</h1>
    <translate v-on:sendapp="getapp"></translate>
    <show v-bind:sendshow="gettext"></show>
  </div>
</template>

<script>
import Translate from './components/Translate'
import Show from './components/Show'

export default {
  name: 'App',
  components: {
    Translate,Show
  },
  data(){
    return{
      gettext:"",
    }
  },
  methods:{
    getapp:function(text,language)
    {
      
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180523T081500Z.2cbe2187ca53b561.81816292eafc61819dd41db8281aef0144c5d936&lang='+language+'&text='+text)
      .then((data)=>{this.gettext=data.body.text[0];})

      
   
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
