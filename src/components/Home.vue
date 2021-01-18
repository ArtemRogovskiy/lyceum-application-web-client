<template>
  <v-app>
    <NavigationBar></NavigationBar>
    <v-main>
      <Carousel></Carousel>
    </v-main>
    <Footer></Footer>
  </v-app>
</template>

<script>
import NavigationBar from "@/components/NavigationBar";
import Carousel from "@/components/Carousel";
import Footer from "@/components/Footer";

export default {
  name: 'Home',
  components: {
    Footer,
    Carousel,
    NavigationBar
  },
  data: () => ({
    drawer: false
  }),
};
</script>