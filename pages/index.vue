<template>
    <div class="bg-img">
      <img :src="indexText.image" alt="">
          <p>
           {{indexText.text}}
          </p>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/about"
          >
            О нас
          </v-btn>
    </div>
</template>

<style scoped>
  .bg-img {
    background:rgba(0,0,0, .4);
    background-size: cover;
    padding: 100px;
    height: 100%;
    width: 100%;
  }

  p {
    z-index: 2;
    position: relative;
  }

  img {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: auto;
  }
</style>

<script>
export default {
  name: 'IndexPage',
  computed: {
    indexText() {
      return this.$store.getters.indexText;
    }
  }
}
</script>
