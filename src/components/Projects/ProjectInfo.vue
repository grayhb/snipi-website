<template>
  <div class="project-info_wrapper">
    <div class="d-flex py-1">
      <v-icon x-large color="yellow darken-2">mdi-alert-octagon</v-icon>
      <div class="ml-4">
        <b>Цель проекта: </b><br />
        <span v-html="item.target"></span>
      </div>
    </div>
    <div class="d-flex py-1">
      <v-icon x-large color="yellow darken-2">mdi-apps</v-icon>
      <div class="ml-4">
        <b>Блок работ: </b><br />
        <span v-html="item.block"></span>
      </div>
    </div>
    <div class="d-flex py-1">
      <v-icon x-large color="yellow darken-2">mdi-clipboard-check</v-icon>
      <div class="ml-4">
        <b>Эффект: </b><br />
        <div v-for="(effect, i) in item.effects" :key="i" class="d-flex my-1">
          <v-icon small>mdi-chevron-right</v-icon>
          <span class="ml-1 project-effect-item" v-html="effect"></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['item']
  //
}
</script>

<style>
.project-info_wrapper {
  font-size: 90%;
}

.project-effect-item {
  line-height: 1;
}
</style>
