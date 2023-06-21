<template>
  <div id="app">
    <h1>PRODUCTOS</h1>
    <br>
    <div class="row">
      <div class="col-md-6">
        <Productos 
        v-bind:infoCards = dtsCards
        v-on:pSeleccionado="procesarPSeleccionado"
        />
      </div>
      <div class="col-md-6">
        <Total 
        v-bind:prdts="arregloProductosSeleccionados"
        v-on:eliminarP="eliminarProducto"
        />
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Productos from './components/Productos.vue'
import Total from './components/Total.vue'
export default {
  name: 'App',
  components: {
    Productos,
    Total
  },
  data:function(){
    return{
      dtsCards:[
        {
          img:'https://imagenes.elpais.com/resizer/sjte0AMDbkud1dQRk2Lv5cUSzmA=/1960x0/cloudfront-eu-central-1.images.arcpublishing.com/prisa/XHFMGAP5PBG37FLDN5FIC4RMBQ.jpg',
          nombre:'KH-7',
          precio:5990
        },
        {
          img:'https://www.oreo-la.com/images/release/products/Jea7pHdCXozWtQlRyLtADuo565rb9m11037SZMLK.png?v=ok',
          nombre:'OREO MINI',
          precio:590
        },
        {
          img:'https://renhetchile.cl/wp-content/uploads/2021/08/1497087.jpg',
          nombre:'COCA COLA',
          precio:2990
        },
        {
          img:'https://latorremx.vtexassets.com/arquivos/ids/173703-300-300?v=1773519481&width=300&height=300&aspect=true',
          nombre:'DETERGENTE ARIEL',
          precio:7990
        },
        {
          img:'https://fontevita.cl/wp-content/uploads/2019/03/aceite_sesamo-600x600.jpg',
          nombre:'ACEITE SÉSAMO',
          precio:10990
        },
        {
          img:'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2cuS-qOAP6QReVGHw0jnPkVo2DOd1hY-m73xXmnwUUywSww9hW1F12YCWFo4UYNQYB_A&usqp=CAU',
          nombre:'AGUA SIN GAS',
          precio:890
        }
      ],
      arregloProductosSeleccionados:[],
    }
  },
    methods:{
      procesarPSeleccionado: function(index){
          let objP = this.dtsCards[index];
          this.arregloProductosSeleccionados.push(objP);
        },
        eliminarProducto: function(index){
          this.arregloProductosSeleccionados.splice(index,1);
        }
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
}</style>
