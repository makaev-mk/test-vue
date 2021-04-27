<template>
  <div class="container pt-1">
    <div class="card">
      <h1>Актульные новости на: {{ dateNews }} </h1>
    </div>
    <AppNews v-for="item in news"
              :title="item"
             :key="item"
    />
  </div>
</template>

<script>
import AppNews from './components/AppNews'

export default {
  name: 'App',
  data() {
    return {
      dateNews : new Date().toLocaleDateString(),
      news: [
        'Официальный курс евро на среду вырос на две копейки',
        'Путин рассчитывает на экспертную проработку мер по реализации послания',
        'ДНР порекомендовала Киеву отказаться от попыток переписать "Минск-2"'
      ]
    }
  },
  methods: {
    open() {
      this.isOpen = !this.isOpen
    }
  },
  components: {
    AppNews
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
