<template>
  <div class="container pt-1">
    <div class="card">
      <h1>Актульные новости на: {{ dateNews }} </h1>
      <span>Открыто: {{ openRate }} | Прочитано: {{ writeNews }}</span>
    </div>
    <AppNews v-for="item in news"
              :title="item.title"
             :id="item.id"
             :is-open="item.isOpen"
             :was-read="item.wasRead"
             @open-news="openRate++"
             @read-news="readNews"
             @unmark="unreadNews"
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
      writeNews: 0,
      openRate: 0,
      dateNews : new Date().toLocaleDateString(),
      news: [
        {
          title: 'Официальный курс евро на среду вырос на две копейки',
          id: 1,
          isOpen:false,
          wasRead: false
        },
        {
          title: 'Путин рассчитывает на экспертную проработку мер по реализации послания',
          id: 2,
          isOpen:false,
          wasRead: false
        },
        {
          title: 'ДНР порекомендовала Киеву отказаться от попыток переписать "Минск-2"',
          id: 3,
          isOpen:false,
          wasRead: false
        }
      ]
    }
  },
  methods: {
    readNews(data) {
      const idx = this.news.findIndex(news=> news.id === data)
      this.news[idx].wasRead = true
      this.writeNews++
    },
    unreadNews(data) {
      const news = this.news.find(news=>news.id === data)
      news.wasRead = false
      this.writeNews--
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
