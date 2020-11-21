<template>
  <v-app>
    <NavigationTop />

    

    <v-main>
      <router-view></router-view>
    </v-main>

    <Footer />
  </v-app>
</template>

<script>

import Footer from './components/shared/footer'
import NavigationTop from './components/shared/navigation-top'

export default {
  name: 'App',
  components: {
    Footer,
    NavigationTop
  },
  data () {
    return {
      
    }
  }
}
</script>
