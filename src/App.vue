<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Динамические и асихронные компоненты</h2>
      <div>
        <app-button @action="active = 'one'"
                    :color="active==='one' ? 'btn-primary' : ''"
        >One</app-button>
        <app-button @action="active = 'two'"
                    :color="active==='two' ? 'btn-primary' : ''"
        >Two</app-button>
      </div>
    </div>
    <app-text-one v-if="active === 'one'"/>
    <app-text-two v-else-if="active === 'two'"/>
  </div>
</template>

<script>
import AppButton from './components/AppButton'
import AppTextOne from './components/AppTextOne'
import AppTextTwo from './components/AppTextTwo'

export default {
  name: 'App',
  data() {
    return {
      active: 'one'
    }
  },
  components: {AppButton, AppTextOne, AppTextTwo}
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
