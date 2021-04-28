<template>
  <hr/>
  <h3>{{ title }}</h3>
  <ul>
    <li v-for="item in news" :key="item.id"> {{ item.title }}</li>
  </ul>
</template>

<script>
export default {
  inject: ['title', 'news']
}
</script>

<style scoped>

</style>
