<template>
  <div class="container pt-1">
    <div class="card">
      <h1>Актульные новости на: {{ dateNews }} </h1>
    </div>
    <AppNews v-for="item in news"
              :title="item.title"
             :id="item.id"
             :is-open="item.isOpen"
             :key="item.id"
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
        {
          title: 'Официальный курс евро на среду вырос на две копейки',
          id: 1,
          isOpen:false
        },
        {
          title: 'Путин рассчитывает на экспертную проработку мер по реализации послания',
          id: 2,
          isOpen:false
        },
        {
          title: 'ДНР порекомендовала Киеву отказаться от попыток переписать "Минск-2"',
          id: 3,
          isOpen:false
        }
      ]
    }
  },
  methods: {
    // open() {
    //   this.isOpen = !this.isOpen
    // }
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
