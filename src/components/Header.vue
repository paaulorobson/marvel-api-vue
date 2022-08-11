<template>
  <div class="marvel-header">
    <div class="marvel-wrapper">
      <img src="../assets/logo.png" alt="logo da marvel">
      <Search />
    </div>
  </div>
</template>

<script>
import Search from '@/components/Search.vue'
export default {
  name: "Header",
  components: {
    Search
  }
}
</script>

<style scoped>
.marvel-header {
  width: 100%;
  background-color: #e62429;
  padding: 1rem 0;
}

.marvel-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
}

.marvel-wrapper img {
  width: 150px;
  height: auto;
}


</style>>
