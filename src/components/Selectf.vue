<script>
export default {
  data() {
    return {
      selected1: null,
      categorias: [
        { text: 'Categoria', value: null, disabled: true },
        { text: 'Coropletas AQI', value: 'aqi' },
        { text: 'Coropletas Crimen', value: 'crimen' },
        { text: 'HotSpots', value: 'hotspot' },
        { text: 'Thiessen Crimen', value: 'thiessenCrimen' },
        { text: 'Thiessen AQI', value: 'thiessenAqi' }
      ],
      selected2: null,
      anios: [
        { text: 'Año', value: null },
        { text: '2016', value: '2016' },
        { text: '2017', value: '2017' },
        { text: '2018', value: '2018' },
        { text: '2019', value: '2019' },
        { text: '2020', value: '2020' },
      ],
      selected3: null,
      meses: [
        { text: 'Mes', value: null },
        { text: 'Enero', value: 'Enero' },
        { text: 'Febrero', value: 'Febrero' },
        { text: 'Marzo', value: 'Marzo' },
        { text: 'Abril', value: 'Abril' },
        { text: 'Mayo', value: 'Mayo' },
        { text: 'Junio', value: 'Junio' },
        { text: 'Julio', value: 'Julio' },
        { text: 'Agosto', value: 'Agosto' },
        { text: 'Septiembre', value: 'Septiembre' },
        { text: 'Octubre', value: 'Octubre' },
        { text: 'Noviembre', value: 'Noviembre' },
        { text: 'Diciembre', value: 'Diciembre' },
      ]
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="row">

      <!-- Primer Select(categorias) -->
      <div class="col-md-auto">
        <select v-model="selected1" class="form-select " aria-label=".form-select-lg example">
          <option v-for="categoria in categorias" :value="categoria.value">
            {{ categoria.text }}
          </option>
        </select>

      <!-- Segundo Select(anio) -->
      </div>
      <div class="col-md-auto">
        <select v-model="selected2" class="form-select " aria-label=".form-select-lg example">
          <option v-for="anio in anios" :value="anio.value">
            {{ anio.text }}
          </option>
        </select>
      </div>

      <!-- Tercer Select(mes) si la categoria lo permite -->
      <div class="col-md-auto" v-if="selected1 === 'aqi' || selected1 === 'crimen' || selected1 === 'hotspot' ">
        <select v-model="selected3" class="form-select " aria-label=".form-select-lg example">
          <option v-for="mes in meses" :value="mes.value">
            {{ mes.text }}
          </option>
        </select>
      </div>
    </div>
  </div>
</template>