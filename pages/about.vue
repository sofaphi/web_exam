<template>
  <v-row>
    <v-col>
      <blockquote class="blockquote">{{aboutText}}</blockquote>
    </v-col>
  </v-row>
</template>


<script>
export default {
  name: 'InspirePage',
  computed: {
    aboutText() {
      return this.$store.getters.aboutText;
    }
  }
}
</script>
