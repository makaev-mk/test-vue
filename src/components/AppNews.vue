<template>
  <div>
    <div class="card mt-2 p-3">
      <h3>{{ title }}</h3>
      <div class="d-flex m-auto">
        <button class="btn" @click="open">
          {{openNews ? 'Закрыть' : 'Открыть'}}
        </button>
        <button class="btn btn-danger"
                v-if="wasRead" @click="$emit('unmark', id)">
          Отменить прочтение
        </button>
      </div>
      <div v-if="openNews">
        <hr/>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate dignissimos eveniet facere id illo ipsum laboriosam magni, nihil nobis non nulla rem repudiandae sit sunt vel velit voluptatibus. Praesentium, quibusdam.</p>
        <button class="btn btn-primary m-3" v-if="!wasRead" @click="mark">Прочесть новость</button>
      </div>
    </div>
  </div>
</template>

<script>
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
  }
}
</script>

<style scoped>

</style>
