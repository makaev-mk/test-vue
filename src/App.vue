<template>
  <div class="container pt-1">
    <div class="card">
      <h1>Актульные новости на: {{ dateNews }} </h1>
    </div>
    <div class="card mt-2 p-3" v-for="item in news" :key="item">
      <h3>{{ item }}</h3>
      <p v-if="isOpen">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate dignissimos eveniet facere id illo ipsum laboriosam magni, nihil nobis non nulla rem repudiandae sit sunt vel velit voluptatibus. Praesentium, quibusdam.</p>
      <button class="btn btn-primary" @click="isOpen = !isOpen">Открыть</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      dateNews : new Date().toLocaleDateString(),
      news: [
          'Путин призвал избегать популизма во время предвыборной кампании',
          'Прививка от пневмококка может облегчить течение коронавируса',
          'Официальный курс евро на среду вырос на две копейки'
      ],
      isOpen: false
    }
  },
  methods: {
    open() {
      this.isOpen = !this.isOpen
    }
  },
  components: {
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
