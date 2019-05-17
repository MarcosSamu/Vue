<template>
  <div id="app">
     <input type="text" v-model="nome">  

     <small>{{status}}</small> <br/><br/>

     {{nome | maiscula()}}

     {{treinado}}
     <input type="button" value="Aperte" @click = "comprimento()">

  </div>
</template>

<script>
  export default{
    name:'exercio',

    data(){
      return{
        nome:'',
        status:'Digite seu nome acima'
      }
    },
    methods:{
      comprimento(){
        return alert('Olá, ' + this.nome)
      },
      terminando(){
        let valor = this.status
        setTimeout(() => {
          if (valor == this.status){
            this.status = ''
          }          
        }, 600)
      }
    },
    watch:{
      nome:function (val_1, val_2) {
        this.status = "Recebendo dados"
        this.terminando()
      }
    },
    filters:{
      maiscula(grande){
        return grande.toUpperCase()
      }
    },
    computed:{
      treinado:{
        get:function(){
          return this.nome.length
        }
      }
    }
  }
</script>