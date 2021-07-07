<template>
  <v-app>
    <NavigationBar></NavigationBar>
    <v-main>
      <Schedule></Schedule>
    </v-main>
    <Footer></Footer>
  </v-app>
</template>

<script>
import Footer from "@/components/Footer";
import Schedule from "@/components/Schedule";
import NavigationBar from "@/components/NavigationBar";

export default {
  name: "SchedulePage",
  components: {Schedule, Footer, NavigationBar}
}
</script>

<style scoped>

</style>