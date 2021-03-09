<template>
  <div class="home">
    <h1>Infectados</h1>
    <article v-for="infectado in $store.state.infectados" :key="infectado.region">
      <h2>{{ infectado.region }}</h2>
      <div>
        Totales: {{ infectado.total }} infectados
      </div>
      <button @click="verRegion(infectado.region, infectado.total)">Ver mas</button>
      <hr>
    </article>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
const  URL_API = 'https://api.apify.com/v2/datasets/hxwow9BB75z8RV3JT/items?format=json&clean=1'
export default {
  name: 'Home',
  components: {

  }, data: function () {
    return {

    }
},
  mounted: function () {
    if (this.$store.state.infectados.length === 0) {
      this.obtenerInfectados();
    }
  },
  methods: {
    obtenerInfectados: function () {
      fetch(URL_API)
      .then (function(response) {
        return response.json();
      })
      .then((json) => {
        this.$store.state.infectados = json[1].regions
      });
    },
    verRegion: function (nombre, total) {
      //modificamos los estados
      this.$store.state.regionTitulo = nombre;
      this.$store.state.regionTotal = total;
      //cambiamos la vista
      this.$router.push('Region');

    }
  }
}
</script>
