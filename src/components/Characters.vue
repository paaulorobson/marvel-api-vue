<template>
  <div class="marvel-container">
    <h1>Personagens</h1>
    <div class="marvel-wrapper">
      <router-link 
      :to="{ name: 'character', params: { id: character.id} }" class="marvel-content" v-for="character in characters" :key="character.id">
        <img class="marvel-characters" :src="`${character.thumbnail.path}.${character.thumbnail.extension}`" :alt="`Foto do ${character.name}`">
        <div class="marvel-description">
          <h3>{{character.name}}</h3>
        </div>
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
  grid-gap: 2rem;
}

.marvel-content {
  background-color: #e62429;
  margin: 10px auto;
  width: 172px;
  box-shadow: 0px 3px 5px 0px rgba(0,0,0,0.75);
  cursor: pointer;
  border-radius: 8px 8px 0 0;
  text-decoration: none;

}

.marvel-characters {
  height: 210px;
  max-width: 172px;
  border-bottom: 3px solid #e62429;
  border-radius: 8px 8px 0 0;
}

.marvel-description {
  background-color: #e62429;
  color: #151515;
  height: 60px;
  padding: 10px;
  white-space: pre-line; 
}

</style>