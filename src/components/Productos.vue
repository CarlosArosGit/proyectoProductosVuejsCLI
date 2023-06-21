<template>
    <div class="productos">
        <div class="container text-center">
            <div class="row">
                <div v-for="(datos, index) in infoCards" :key="index" class="col">
                    <div class="card" style="width: 18rem;">
                        <img v-bind:src="datos.img" class="card-img-top" alt="...">
                        <div class="card-body">
                            <h5 class="card-title">{{ datos.nombre }}</h5>
                            <p class="card-text">${{ datos.precio }}</p>
                            <a href="#" class="btn btn-primary" v-on:click.prevent="addP(index)">Agregar</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    name: 'Productos',
    props: {
        infoCards: {
            type: Array,
            required: true
        }
    },
    methods:{
        addP: function(index){
            this.$emit('pSeleccionado', index);
        }
    }
}
</script>

<style scoped>
img {
    width: 100%;
    height: 200px;
}

h5 {
    font-weight: 600;
}

.card {
    margin-top: 50px;
}
</style>
  