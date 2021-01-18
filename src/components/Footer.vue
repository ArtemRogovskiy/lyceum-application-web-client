<template>
  <div>
    <p></p>
    <v-footer class="pa-3 justify-center" :absolute=true>
      <div>&copy; {{ new Date().getFullYear() }} - </div>
      <v-btn href="https://firstlyceum.by/" target="_blank" text>
        <span class="mr-2">МГОЛ 1</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-footer>
  </div>
</template>

<script>

export default {
  name: "Footer",
}

</script>
