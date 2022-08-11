<template>
  <div class="marvel-container">
    <router-link to="/" class="marvel-back">
      <img src="../assets/arrow_back.svg" alt="">
      <p>Voltar</p>
    </router-link>
    <div class="marvel-wrapper">
      <div v-for="char in character" :key="char.id">
        <h1>{{char.name}}</h1>

        <template v-if="possuiDescricao">
          <p>{{char.description}}</p>
        </template>

        <template v-else>
          <p>O personagem não possui uma descrição detalhada.</p>
        </template>
      </div>

      <div>
        <img :src="url" alt="Foto do personagem">
      </div>
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
      image: state => state.url

    }),

    possuiDescricao() {
      return this.character.description == '' ? true : false
    }
  },

  methods: {
    getImage() {
      this.url = `${this.image}${this.size}`
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

.marvel-back {
  text-decoration: none;
  color: #fff;
  display: flex;
  align-items: flex-end;
  position: relative;
}

.marvel-back img {
  margin-top: 1rem;
  width: 2rem;
}

.marvel-back p {
  font-size: 1.5rem;
  font-weight: bold;
  text-transform: uppercase;
}

.marvel-container h1 {
  margin: 1rem 0;
  color: #fff;
  text-transform: uppercase;
  font-family: 'Anton', cursive;
}

.marvel-wrapper {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  gap: 8rem;
  margin-top: 5rem;
}

.marvel-wrapper p {
  color: #fff;
  font-size: 1.2rem;
}

.marvel-wrapper img {
  width: 300px;
  height: auto;
}
</style>