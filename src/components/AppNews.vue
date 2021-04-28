<template>
  <div>
    <div class="card mt-2 p-3">
      <h3>{{ title }}</h3>
      <p v-if="openNews">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate dignissimos eveniet facere id illo ipsum laboriosam magni, nihil nobis non nulla rem repudiandae sit sunt vel velit voluptatibus. Praesentium, quibusdam.</p>
      <button class="btn" @click="open">Открыть</button>
    </div>
  </div>
</template>

<script>
export default {
  // props: ['title'],
  props: {
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
    }
  },
  data() {
    return {
      openNews: this.isOpen
    }
  },
  methods: {
    open() {
      this.openNews = !this.openNews
    }
  }
}
</script>

<style scoped>

</style>
