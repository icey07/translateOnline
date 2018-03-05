<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单/易用/便捷</h5>
    <translateForm @formSubmit="tranlateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function(){
   return {
    translatedText:''
 }
},
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods:{
    tranlateText(text,language){
    this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180122T143210Z.aa7733a46bbb97ee.517c8356c2747db7082cc3655b3747576e8f10b0&lang='+language+'&text='+text).then((response)=>{
        this.translatedText=response.body.text[0]
      })
     }
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
