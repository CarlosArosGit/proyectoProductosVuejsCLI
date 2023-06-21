<template>
    <div class="total">
        <h2>TOTAL A PAGAR <i class="bi bi-cart"></i></h2>
        <hr>
        <div class="row">
            <div class="col-md-4">
                <p>NOMBRE PRODUCTO</p>
            </div>
            <div class="col-md-4">
                <p>PRECIO</p>
            </div>
            <div class="col-md-4">
                <p>ELIMINAR</p>
            </div>
        </div>
        <div class="row" v-for="(info, index) in prdts" v-bind:key="index">
            <div class="col-md-4">
                <p>{{ info.nombre }}</p>
            </div>
            <div class="col-md-4">
                <p>${{ info.precio }}</p>
            </div>
            <div class="col-md-4">
                <button class="btn btn-danger" v-on:click.prevent="eliminar(index)"><i class="bi bi-trash"></i></button>
            </div>
        </div>
        <button class="btn btn-primary" v-on:click.prevent="calcularCosto" id="btnCalcular"> Calcular total a Pagar</button>
        <div v-if="mostrar==true">
            <p>El subtotal es: ${{  acumulado }}</p>
            <p>El iva es: ${{  iva }}</p>
            <p><strong>El valor final a pagar es: ${{  valorFinalAPagar }}</strong></p>
        </div>
    </div>
</template>
  
<script>
export default {
    name: 'Total',
    props: {
        prdts:{
            type: Array,
            required:true,
        }
    },
    data:function(){
        return{
            acumulado:0,
            iva: 0,
            valorFinalAPagar:0,
            mostrar: false,
        }
    },
    methods:{
        calcularCosto: function(){
            for(let datos of this.prdts) {
                this.acumulado = this.acumulado + datos.precio;
            }
            this.calcularIva();
            this.mostrar = true;
            let btnCalcular = document.getElementById('btnCalcular');
            btnCalcular.disabled = true;
        },
        calcularIva:function(){
            this.iva = this.acumulado*19/100;
            this.iva =  Math.round(this.iva);
            this.valorFinalAPagar = this.acumulado + this.iva;
        },
        eliminar: function(index){
            this.mostrar = false;
            let btnCalcular = document.getElementById('btnCalcular');
            btnCalcular.disabled = false;
            this.acumulado = 0;
            this.$emit('eliminarP', index);
        }
    }
}
</script>

<style scoped>
h2 {
    margin-top: 50px;
}</style>
  