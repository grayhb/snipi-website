<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      src="@/assets/img/bgHero.jpg"
      class="drawer-wrapper"
    >
      <v-list>
        <v-list-item>
          <v-list-item-avatar color="white" size="28">
            <v-img src="@/assets/img/snipi-logo.png" alt="Logo"></v-img>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title">{{ companyName }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider />

      <v-list dense>
        <v-list-item
          v-for="([icon, text, link], i) in items"
          :key="i"
          link
          @click="$vuetify.goTo(link)"
        >
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app :color="color" :flat="flat" class="px-2" :class="{ expand: flat }">
      <div class="d-flex align-center">
        <a href="./">
          <v-avatar color="white" size="32">
            <v-img src="@/assets/img/snipi-logo.png" />
          </v-avatar>
        </a>
        <div class="company-name">
          {{ companyName }}
        </div>
      </div>
      <v-spacer />
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="mr-4" v-if="isXs" />
      <div v-else>
        <v-btn
          v-for="([icon, text, link], i) in items"
          :key="link"
          text
          @click="$vuetify.goTo(link)"
        >
          <span class="mr-2">{{ text }}</span>
        </v-btn>
      </div>
    </v-app-bar>
  </div>
</template>

<script>
import { SITE } from '../configs/const'

export default {
  computed: {
    companyName() {
      return SITE.companyName
    },
    items() {
      return SITE.pages
    }
  },
  data: () => ({
    drawer: null,
    isXs: false
  }),
  props: {
    color: String,
    flat: Boolean
  },
  methods: {
    onResize() {
      this.isXs = window.innerWidth < 850
    }
  },

  watch: {
    isXs(value) {
      if (!value) {
        if (this.drawer) {
          this.drawer = false
        }
      }
    }
  },
  mounted() {
    this.onResize()
    window.addEventListener('resize', this.onResize, { passive: true })
  }
}
</script>

<style scoped>
.v-toolbar {
  transition: 0.6s;
}

.expand {
  height: 80px !important;
  padding-top: 10px;
}

.title {
  font-size: 75% !important;
  line-height: 1;
}

.company-name {
  line-height: 1;
  font-weight: 600;
  font-size: 1rem;
  margin-left: 16px;
}

.drawer-wrapper {
  background-color: white;
  height: 100% !important;
}

@media only screen and (max-width: 600px) {
  .company-name {
    font-size: 0.95rem;
  }
}
</style>
