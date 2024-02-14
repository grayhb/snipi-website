<template>
  <section id="about">
    <v-container>
      <v-row>
        <v-col cols="12">
          <div class="py-1">
            <h1>{{ pageTitle }}</h1>
          </div>
          <div></div>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="6">
          <v-card>
            <v-card-title>ФУНКЦИОНАЛ</v-card-title>
            <v-card-text class="black--text">
              <div v-for="(item, i) in functionals" :key="i" class="d-flex align-center">
                <v-icon color="amber accent-2">mdi-stop</v-icon>
                <div class="ml-4 my-1 functional-item__text">
                  {{ item }}
                </div>
              </div>
            </v-card-text>
          </v-card>
          <v-card class="mt-5 about-projects">
            <v-card-title>ПРИМЕРЫ РЕШЕНИЙ</v-card-title>
            <v-card-text>
              <v-btn
                v-for="item in projects"
                :key="'btn_' + item.id"
                class="mb-1"
                color="amber accent-2"
                @click="$vuetify.goTo('#' + item.id)"
                depressed
                small
                block
              >
                {{ item.name }}
              </v-btn>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="12" md="6">
          <v-card>
            <v-card-title>СТЕК ТЕХНОЛОГИЙ</v-card-title>
            <v-container class="px-6 pb-6">
              <v-row>
                <v-col
                  class="stack-wrapper px-1 py-0"
                  v-for="(stack, i) in stackGroups"
                  :key="'stackGroup_' + i"
                  cols="6"
                  md="6"
                >
                  <div class="stack-group">
                    <div class="stack-name">
                      {{ stack.name }}
                    </div>
                    <div
                      class="d-flex align-center my-1"
                      v-for="(stackName, j) in stack.items"
                      :key="'stackName' + i + '_' + j"
                    >
                      <v-icon x-small color="amber accent-2"> mdi-record</v-icon>
                      <span class="ml-1 stack-item-name">{{ stackName }}</span>
                    </div>
                  </div>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves">
      <img src="~@/assets/img/wave2.svg" />
    </div>
  </section>
</template>

<script>
import { SITE } from '../configs/const'

export default {
  computed: {
    pageTitle() {
      return SITE.automatisation.pageTitle
    },
    functionals() {
      return SITE.automatisation.functionals
    },
    stackGroups() {
      return SITE.automatisation.stackGroups
    },
    projects() {
      return SITE.projects.items
    }
  }
}
</script>

<style scoped>
.svg-border-waves img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}

#about {
  z-index: 0;
}

.functional-item__text {
  line-height: 1.25;
}

.stack-wrapper {
  line-height: 1.25;
}

.stack-item-name {
  font-size: 0.8rem;
  line-height: 1.2;
}

.stack-item-name:hover,
.functional-item__text:hover {
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.2);
  cursor: default;
}

.stack-name {
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  margin-bottom: 4px;
  min-height: 3rem;
  color: #222222;
}
</style>

<style>
@media only screen and (max-width: 1260px) {
  .about-projects .v-btn {
    font-size: 75%;
  }
}

@media only screen and (max-width: 600px) {
  .about-projects .v-btn {
    font-size: 65%;
  }

  .stack-name {
    font-size: 90%;
  }
}
</style>
