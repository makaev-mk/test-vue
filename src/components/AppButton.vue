<template>
 <button class="btn" :class="color" @click="$emit('action')">
   <slot/>
 </button>
</template>

<script>
export default {
  emits:['action'],
  props: {
    color: {
      type: String,
      default: '',
      validator(value){
       return ['', 'btn-primary', 'btn-danger'].includes(value)
      }
    }
  }
}
</script>

<style scoped>

</style>
