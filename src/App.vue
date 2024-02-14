<template>
  <v-app>
    <navigation :color="color" :flat="flat" />
    <v-main class="pt-0">
      <home />
      <about />
      <projects />
    </v-main>
    <v-scale-transition>
      <v-btn
        fab
        v-show="fab"
        v-scroll="onScroll"
        fixed
        bottom
        right
        color="secondary"
        @click="toTop"
      >
        <v-icon color="black">mdi-arrow-up</v-icon>
      </v-btn>
    </v-scale-transition>
    <siteFooter />
  </v-app>
</template>

<style scoped>
.v-main {
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
}
</style>

<script>
import navigation from './components/Navigation'
import siteFooter from './components/Footer'
import home from './components/HomeSection'
import about from './components/AboutSection'
import projects from './components/ProjectsSection'

export default {
  name: 'App',

  components: {
    navigation,
    home,
    about,
    projects,
    siteFooter
  },

  data: () => ({
    fab: null,
    color: '',
    flat: null
  }),

  created() {
    const top = window.pageYOffset || 0
    if (top <= 60) {
      this.color = 'transparent'
      this.flat = true
    }
  },

  watch: {
    fab(value) {
      if (value) {
        this.color = 'secondary'
        this.flat = false
      } else {
        this.color = 'transparent'
        this.flat = true
      }
    }
  },

  methods: {
    onScroll(e) {
      if (typeof window === 'undefined') return
      const top = window.pageYOffset || e.target.scrollTop || 0
      this.fab = top > 60
    },
    toTop() {
      this.$vuetify.goTo(0)
    }
  }
}
</script>
