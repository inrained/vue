<template>
  <form v-on:submit="send">
    <input type="text" placeholder="请输入要翻译的内容" v-model="inputtext">
    <select v-model="language">
        <option value="en">English</option>
        <option value="ru">Russian</option>
        <option value="ko">Korean</option>

     </select> 
    <input type="submit" value="翻译">
  </form>
</template>

<script>


export default {
  name: 'translate',
  components: {
  
  },
  data(){
    return{
      inputtext:"",
      language:"en"
    }
  },
  methods:{
    send:function(e)
    { 
      this.$emit("sendapp",this.inputtext,this.language); 
      e.preventDefault();// 取消默认事件，防止点击以后再默认刷新一次
    }
  }
}

</script>

<style>

</style>
