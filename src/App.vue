<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <textarea v-model="usertextarea">

    </textarea>
    <p v-html='userWasm'></p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      usertextarea:'#  dwdwd',
      userWasm:''
    }
  },
  watch:{
    usertextarea(value){
      import('./pkg').then(wasm=>{
       this.userWasm =  wasm.greet(value)
      })
    }
  },
  mounted() {
    import('./pkg').then(wasm=>{
      console.log(wasm.greet(this.usertextarea),wasm);
    })
  },
  computed:{
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
