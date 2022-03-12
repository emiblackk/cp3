<template>
<div>
  <div class="wrapper">
    <div class="search">
      <form class="pure-form">
        <i class="fas fa-search"></i><input v-model="searchText" />
      </form>
    </div>
  </div>
  <RecipeList :recipes="recipes" />
  <footer>
    <p><a href="https://github.com/emiblackk/cp3.git">Repo</a></p>
  </footer>
</div>
</template>

<script>
import RecipeList from "../components/RecipeList.vue"
export default {
  name: 'Home-view',
  components: {
    RecipeList
  },
  data() {
    return {
      searchText: '',
    }
  },
  computed: {
    recipes() {
      return this.$root.$data.recipes.filter(recipe => recipe.name.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
    }
  },
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}
</style>
