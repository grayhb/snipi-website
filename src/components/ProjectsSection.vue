<template>
  <section id="projects">
    <v-container class="">
      <v-row>
        <v-col cols="12" class="py-0 mt-4">
          <div class="pb-1">
            <h1>{{ pageTitle }}</h1>
          </div>
          <div></div>
        </v-col>
      </v-row>
      <v-row v-for="(item, i) in items" :key="item.id" :id="item.id">
        <v-col cols="12" md="6">
          <h3>{{ item.name }}</h3>
          <div class="subtitle-1 mb-2 project-subtitle">{{ item.details }}</div>

          <div class="d-flex flex-wrap my-1 project-tags_wrapper">
            <div
              v-for="(tag, i) in item.tags"
              :key="'tag_' + item.id + '_' + i"
              class="d-flex align-center mr-2"
              small
            >
              <v-icon small color="amber darken-2" class="mr-1"> mdi-bookmark </v-icon>
              {{ tag }}
            </div>
          </div>
          <project-info :item="item" />
        </v-col>
        <v-col cols="12" md="6">
          <project-images :item="item" />
        </v-col>

        <v-col v-if="i < items.length - 1" cols="12">
          <v-divider></v-divider>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<script>
import { SITE } from '../configs/const'
import projectInfo from './Projects/ProjectInfo'
import projectImages from './Projects/ProjectImages'

export default {
  components: { projectInfo, projectImages },
  computed: {
    pageTitle() {
      return SITE.projects.pageTitle
    },
    items() {
      return SITE.projects.items
    }
  }
}
</script>

<style scoped>
#projects {
  background-color: #f4f7f5;
  padding-bottom: 24px;
}
.project-tags_wrapper {
  font-size: 80%;
  cursor: default;
  color: #666666;
}

.project-subtitle {
  line-height: 1.2;
}
</style>
