<template>
  <v-app>
    <NavigationBar></NavigationBar>
    <p></p>
    <v-card class="mx-auto">
      <v-container>
        <v-row dense>
          <v-col v-for="(newsItem, i) in newsItems" :key="i" cols="12">
            <v-card :color="'#'+(Math.random()*0xFFFFFF<<0).toString(16)" dark>
              <v-card-title class="headline" v-text="newsItem.title"></v-card-title>
              <v-card-subtitle v-text="newsItem.message"></v-card-subtitle>
              <v-card-actions v-text="newsItem.createdTime"></v-card-actions>
<!--              <v-avatar class="ma-3" size="125" tile>-->
<!--                <v-img :src="newsItem.src"></v-img>-->
<!--              </v-avatar>-->
            </v-card>
          </v-col>

        </v-row>
      </v-container>
    </v-card>

    <Footer></Footer>
  </v-app>
</template>

<script>
import NavigationBar from "@/components/NavigationBar";
import Footer from "@/components/Footer";
import axios from "axios";

export default {
  name: "NewsCard",
  components: {Footer, NavigationBar},

  data: () => ({
    newsItems: [
      // {
      //   src: 'https://cdn.vuetifyjs.com/images/cards/foster.jpg',
      //   title: 'Supermodel',
      //   artist: 'Foster the People',
      // },
      // {
      //   src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
      //   title: 'Halcyon Days',
      //   artist: 'Ellie Goulding',
      // },
    ],
  }),

  created() {
    console.log('in creted() method')
    axios.get(`http://localhost:8088/news`)
        .then(response => {
          console.log(response.data)
          this.newsItems = response.data
        })
        .catch(e => {
          console.log(e)
          this.errors.push(e)
        })
  }
}
</script>

<style scoped>

</style>