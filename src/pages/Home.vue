<template>
  <div class="marvel-container">
    <Characters />
 </div>
</template>

<script>
import Characters from '@/components/Characters.vue'
export default {
  name: "Home",
  components: {
    Characters,
  }
}
</script>


<style scoped>
.marvel-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;

}

</style>