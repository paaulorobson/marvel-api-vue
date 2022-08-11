<template>
  <div class="marvel-search">
    <input type="text" placeholder="Buscar personagem" />
    <img src="../assets/search.svg" alt="icone de pesquisa">
  </div>
</template>

<script>
export default {
  name: "Search",
}
</script>

<style scoped>

.marvel-search {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #fff;
  width: 300px;
  height: 40px;
  border-radius: 4px;
  box-shadow: 0px 3px 5px 0px rgba(0,0,0,0.75);
  padding: 0 10px;

}
.marvel-search input{
  outline: none;
}

.marvel-search img {
  color: #151515;
}

::placeholder {
  padding: 0 10px;
}
</style>