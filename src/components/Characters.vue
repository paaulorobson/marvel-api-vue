<template>
  <div class="marvel-container">
    <h1>Personagens</h1>
    <div class="marvel-wrapper">
      <router-link 
      :to="{ name: 'character', params: { id: character.id} }" class="marvel-content" v-for="character in characters" :key="character.id">
        <img class="marvel-characters" :src="`${character.thumbnail.path}.${character.thumbnail.extension}`" :alt="`Foto do ${character.name}`">
        
        <h3>{{character.name}}</h3>
      </router-link>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'Characters',

  mounted() {
    this.$store.dispatch('getCharacters')
  },

  computed: {
    ...mapState({
      characters: state => state.characters,
    })
  },

}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Anton&family=Silkscreen:wght@400;700&display=swap');

.marvel-container h1 {
  margin: 1rem 0;
  color: #fff;
  text-transform: uppercase;
  font-family: 'Anton', cursive;
}

.marvel-wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-auto-rows: 250px;
  grid-gap: 2.5rem;
  padding: 0 0 5rem 0;
}

.marvel-content {
  cursor: pointer;
  text-decoration: none;
}

.marvel-content h3 {
  width: 172px;
  background-color: #e62429;
  padding: 1rem;
  color: #fff;
  margin-top: -10px;
  white-space: pre-line; 
}

.marvel-characters {
  height: 210px;
  max-width: 172px;
  border-radius: 8px 8px 0 0;
}

</style>