<template>
 <button class="btn" :class="color" @click="$emit('action')">
    {{ text }}
 </button>
</template>

<script>
export default {
  emits:['action'],
  props: {
    text: {
      type: String,
      required: true
    },
    color: {
      type: String,
      default: '',
      validator(value){
       return ['', 'btn-primary m-3', 'btn-danger'].includes(value)
      }
    }
  }
}
</script>

<style scoped>

</style>
