<template>
  <v-carousel>
    <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
        reverse-transition="fade-transition"
        transition="fade-transition"
    ></v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: "Carousel",
  data() {
    return {
      items: [
        {
          src: 'https://firstlyceum.by/sites/default/files/images/stories/news/liceum-1.jpg',
        },
        {
          src: 'https://firstlyceum.by/sites/all/themes/professional_theme/images/slide-image-5.jpg',
        },
        {
          src: 'https://firstlyceum.by/sites/all/themes/professional_theme/images/slide-image-2.jpg',
        },
      ],
    }
  },
}
</script>