<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Динамические и асихронные компоненты</h2>
      <div>
        <app-button @action="active = 'one'"
                    :color="oneColor"
        >One</app-button>
        <app-button @action="active = 'two'"
                    :color="twoColor"
        >Two</app-button>
      </div>
    </div>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
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
  mounted() {
    setTimeout(()=>{
      this.componentName = 'new comp name'
    }, 1500)
  }
  ,
  computed: {
    // componentName() {
    //   return 'app-text-' + this.active
    // },
    componentName: {
      get() {
        return 'app-text-' + this.active
      },
      set(value) {
        console.log('compo', value)
      }
    },
    oneColor() {
      return this.active === 'one' ? 'btn-primary' : ''
    },
    twoColor() {
      return this.active === 'two' ? 'btn-primary' : ''
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
