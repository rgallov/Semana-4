<template>
  <div>
    <div class="container-fluid">
      <div class="row mt-md-5 mt-sm-5 mt-xs-5">
        <div
          v-for="(art, indice) of datos"
          :key="art.id"
          class="col-lg-6 col-xs-12 border"
        >
          <div v-if="indice <= 3">
            <div class="d-flex justify-content-center align-items-center">
              <div class="p-3">
                <img src="https://simaro.global.ssl.fastly.net/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/P/a/Paso-N--16-Galn-2-Compartimiento-de-Basura-y-de-Reciclaje---Disponible-en-Varios-Colores_2.jpeg" class="imagen_producto"/>
              </div>

              <div class="p-2">
                <p>
                  <h5>Producto:</h5>
                </p>
                <p>
                  {{ art.nombre }}
                </p>
                <p>
                  <h5>Descripción:</h5>
                </p>
                <p>
                  {{ art.descripcion }}
                </p>
              </div>              
            </div>
            <div class="d-flex container-fluid justify-content-end pb-2 mt-n2">
              <button type="button" class="btn btn-outline-info">Info</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <section
      id="news-events"
      data-section-name="casos-exito"
      class=""
    >
      <div class="container col-sm-12 col-md-12 col-lg-12 col-xl-12">
        <div class="dark col-sm-12 col-md-12 col-lg-12 col-xl-12">
          <h2 class="bold">Casos de Exito</h2>
        </div>
      </div>

      <div class="container-fluid">
        <div class="row justify-content-center mb-5">
          <CasoCard
            v-for="miembro in casos"
            :key="miembro.codigo"
            :member="miembro"
            class="col mt-5"
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
export default {
  components: {
    CasoCard,
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


</style>
