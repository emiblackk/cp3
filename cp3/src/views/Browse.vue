<template>
<div>
  <RecipeList :recipes="recipes" />


  <div class="info">
    <h1>{{this.$root.$data.selected_recipe.name}} </h1>
    <h2>{{this.$root.$data.selected_recipe.average_rating}} stars</h2>
  </div>
  <div class="image">
    <img :src="'/images/recipes/'+this.$root.$data.selected_recipe.image">
  </div>
  <div class="price">
  <h1>Directions</h1>
    <p>{{this.$root.$data.selected_recipe.recipe}}</p>

    <button class="auto" @click="myMethod()">Save Recipe</button>

  </div>

  <footer>
    <p><a href="https://github.com/emiblackk/cp3.git">Repo</a></p>
  </footer>
</div>
</template>

<script>
import RecipeList from "../components/RecipeList.vue"
export default {
  name: 'Browse-view',
  components: {
    RecipeList
  },
  data() {
    return {
      country: '',
    }
  },
  computed: {
    recipes() {
      return this.$root.$data.recipes.filter(recipe => recipe.country === this.country);
    }
  },
  methods: {
    myMethod: function myMethod() {
      console.log("HERE")
      console.log(this.$root.$data.selected_recipe)
      this.$root.$data.cart.push(this.$root.$data.selected_recipe);
    }
  },
}
</script>
