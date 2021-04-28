<template>
  <div>
    <div class="card mt-2 p-3">
      <h3>{{ title }}</h3>
      <div class="d-flex m-auto">
        <app-button  @action="open">
          {{ openNews ? 'Закрыть' : 'Открыть' }}
        </app-button>
        <app-button v-if="wasRead"
                    color="btn-danger"
                    @action="$emit('unmark', id)">
          Отменить прочтение
        </app-button>
      </div>
      <div v-if="openNews">
        <hr/>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate dignissimos eveniet facere id illo ipsum laboriosam magni, nihil nobis non nulla rem repudiandae sit sunt vel velit voluptatibus. Praesentium, quibusdam.</p>
        <app-button color="btn-primary m-3"
                    v-if="!wasRead"
                    @action="mark">
          Прочесть новость
        </app-button>
        <AppNewsList/>
      </div>
    </div>
  </div>
</template>

<script>
import AppButton from './AppButton'
import AppNewsList from './AppNewsList'

export default {
  // props: ['title'],
  // emits: ['open-news'],
  emits: {
    'open-news': null,
    'read-news': null,
    'unmark': null
  },
  props: {
    wasRead: Boolean,
    title: {
      type: String,
      required:true
    },
    id: {
      type: Number,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false
    },
  },
  data() {
    return {
      openNews: this.isOpen
    }
  },
  methods: {
    open() {
      this.openNews = !this.openNews
      if (this.openNews) {
        this.$emit('open-news')
      }
    },
    mark() {
      this.openNews = false
      this.$emit('read-news', this.id)
    },
    // unmark() {
    //   this.$emit('unmark', this.id)
    // }
  },
  components: {
    AppButton,
    AppNewsList
  }
}
</script>

<style scoped>

</style>
