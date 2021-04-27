<template>
  <div>
    <div class="card mt-2 p-3">
      <h3>{{ title }}</h3>
      <p v-if="isOpen">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cupiditate dignissimos eveniet facere id illo ipsum laboriosam magni, nihil nobis non nulla rem repudiandae sit sunt vel velit voluptatibus. Praesentium, quibusdam.</p>
      <button class="btn" @click="isOpen = !isOpen">Открыть</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title'],
  data() {
    return {
      isOpen: false
    }
  }
}
</script>

<style scoped>

</style>
