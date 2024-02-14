<template>
  <div class="h-100 d-flex align-center justify-center">
    <v-carousel height="350">
      <v-carousel-item v-for="(item, i) in images" :key="i">
        <v-img :src="item" height="350" contain />
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  props: ['item'],
  computed: {
    images() {
      return this.item.images.map((e) => {
        return `./img/${this.item.id}/${e}`
      })
    }
  }
}
</script>

<style>
.h-100 {
  height: 100%;
}
</style>
