<template>
  <v-app>
    <NavigationBar></NavigationBar>
    <p></p>
    <v-card class="mx-auto">
      <v-container>
        <v-row dense>
          <v-col cols="12">
            <v-card color="#385F73" dark>
              <v-card-title class="headline">Unlimited music now</v-card-title>
              <v-card-subtitle>Listen to your favorite artists and albums whenever and wherever, online and offline.
              </v-card-subtitle>
              <v-card-actions>
                <v-btn text>Listen Now</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <v-col v-for="(newsItem, i) in newsItems" :key="i" cols="12">
            <v-card :color="'#'+(Math.random()*0xFFFFFF<<0).toString(16)" dark>
              <div class="d-flex flex-no-wrap justify-space-between">
                <div>
                  <v-card-title class="headline" v-text="newsItem.title"></v-card-title>
                  <v-card-subtitle v-text="newsItem.artist"></v-card-subtitle>
                  <v-card-actions>
                    <v-btn class="ml-2 mt-5" outlined rounded small>
                      START RADIO
                    </v-btn>
                  </v-card-actions>
                </div>
                <v-avatar class="ma-3" size="125" tile>
                  <v-img :src="newsItem.src"></v-img>
                </v-avatar>
              </div>
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

export default {
  name: "NewsCard",
  components: {Footer, NavigationBar},

  data: () => ({
    newsItems: [
      {
        src: 'https://cdn.vuetifyjs.com/images/cards/foster.jpg',
        title: 'Supermodel',
        artist: 'Foster the People',
      },
      {
        src: 'https://cdn.vuetifyjs.com/images/cards/halcyon.png',
        title: 'Halcyon Days',
        artist: 'Ellie Goulding',
      },
    ],
  }),
}
</script>

<style scoped>

</style>