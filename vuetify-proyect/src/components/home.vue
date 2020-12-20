<template>
  <div>
    <section id="products">
      <div class="container col-sm-12 col-md-12 col-lg-12 col-xl-12">
        <h2 class="bold">Productos</h2>
      </div>
      <div class="container-fluid">
        <div class="row">
          <div
            v-for="(art, indice) of datos"
            :key="art.id"
            class="col-lg-6 col-xs-12 border"
          >
            <div v-if="indice <= 3">
                <articulo-data :articulo=art></articulo-data>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section
      id="cases"
      data-section-name="casos-exito"
    >
      <div class="container col-sm-12 col-md-12 col-lg-12 col-xl-12">
        <h2 class="bold">Casos de Exito</h2>
      </div>

      <div class="container-fluid">
        <div class="d-flex flex-row flex-nowrap overflow-auto">
          <CasoCard
            v-for="miembro in casos"
            :key="miembro.codigo"
            :member="miembro"
            class="col mt-1"
          ></CasoCard>
        </div>
      </div>      
    </section>
  </div>
</template>

<script>
import axios from "axios";
import CasoCard from "./CasoCard.vue";
import jsonCasos from "../assets/files/casosExito.json";
import ArticuloData from './ArticuloData.vue';
export default {
  components: {
    CasoCard,
    ArticuloData,
  },
  data() {
    return {
      datos: null,
      casos: jsonCasos.casos,
    };
  },
  mounted() {
    axios.get("articulo/list").then((response) => (this.datos = response.data));
  },
  
};

</script>
<style scoped>
.imagen_producto{
    width: 80%;
}

.bold{
  font-family: Helvetica, "Trebuchet MS", Verdana, sans-serif;
}

</style>
