<template>
  <div class="marvel-container">
    <div v-for="char in character" :key="char.id">
      <h1>{{char.name}}</h1>

        <template v-if="naoPossuiDescricao">
          <h3> Não possui uma descrição</h3>
        </template>
        <template v-else>
          <p>{{char.description}}</p>
        </template>
     
    </div>

    <div>
      <img :src="url" alt="Foto do personagem">
    </div>
  </div>
</template>

<script>
import { mapState  } from 'vuex'

export default {
  name: 'Character',

  data() {
    return {
      url:'',
      size: 'standard_large.jpg'
    }
  },

  mounted() {
    this.$store.dispatch('getCharacter', this.$route.params.id)

    this.getImage()
  },

  computed: {
    ...mapState({
      character: state => state.character,
      preUrl: state => state.url
    }),

    naoPossuiDescricao() {
      return this.character.description == '' ? false : true
    }
  },

  methods: {
    getImage() {
      this.url = `${this.preUrl}${this.size}`
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Anton&family=Silkscreen:wght@400;700&display=swap');

.marvel-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  height: 100vh;
}

.marvel-container h1 {
  margin: 1rem 0;
  color: #fff;
  text-transform: uppercase;
  font-family: 'Anton', cursive;
}

</style>