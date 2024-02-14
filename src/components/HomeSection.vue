<template>
  <section id="home">
    <v-parallax src="@/assets/img/bgHero.jpg" height="300">
      <v-container>
        <v-row align="center" justify="center">
          <v-col cols="12">
            <v-row align="center" justify="center">
              <v-col cols="12" md="12" xl="12">
                <div class="company-content">
                  <!-- <h1 class="font-weight-bold mb-4 text-no-wrap home-company-name">
                    {{ companyName }}
                  </h1> -->
                  <h3
                    v-for="(infoItem, i) in companyInfoItems"
                    :key="'info_' + i"
                    class="font-weight-light my-2 d-flex align-center"
                  >
                    <v-icon class="mr-2" dense>mdi-chevron-right</v-icon>
                    <span v-html="infoItem"></span>
                  </h3>
                </div>
              </v-col>
              <v-col cols="12" md="6" xl="4" class="hidden-sm-and-down"> </v-col>
            </v-row>
          </v-col>
        </v-row>
        <div class="svg-border-waves text-white">
          <v-img src="@/assets/img/borderWaves.svg" />
        </div>
      </v-container>
    </v-parallax>
    <v-container>
      <v-row>
        <v-col cols="12">
          <div v-for="(item, i) in companyDetailItems" :key="i" class="py-1 mb-1">
            <h3>{{ item.title }}</h3>
            <span>{{ item.text }}</span>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<script>
import { SITE } from '../configs/const'

export default {
  computed: {
    companyName() {
      return SITE.companyName
    },
    companyInfoItems() {
      return SITE.companyInfoItems
    },
    companyDetailItems() {
      return SITE.companyDetailItems
    }
  }
}
</script>

<style>
.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}

#home {
  z-index: 0;
  color: black !important;
}

.company-content {
  color: rgb(40, 40, 40);
  margin-top: 50px;
}

section {
  position: relative;
}

@media only screen and (max-width: 600px) {
  .home-company-name {
    font-size: 1.3rem;
  }

  #home {
    font-size: 80% !important;
  }

  .company-content {
    margin-top: 0px;
  }
}
</style>
