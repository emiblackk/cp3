<template>
<div class="wrapper">
  <div class="recipes">
    <div class="recipe" v-for="recipe in recipes" :key="recipe.id">
      <div class="info">
        <h1>{{recipe.name}}</h1>
        <p>{{recipe.country}}</p>
      </div>
      <div class="image">
        <img :src="'/images/recipes/'+recipe.image">
      </div>
      <div class="price">
        <h2>{{recipe.price}}</h2>
        <button class="auto" @click="otherMethod(recipe)">View Recipe</button>

        <button class="auto" @click="myMethod(recipe)">Remove Item</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'RecipeList',
  props: {
    recipes: Array,
  },
  methods: {
    myMethod: function myMethod(ev) {
      this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(ev), 1);
    },
    otherMethod: function otherMethod(ev) {
    this.$root.$data.selected_recipe = ev;
    console.log(this.$root.$data.selected_recipe)
      this.$router.push({ path: '/Browse' });

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

.recipes {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.recipe {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.recipe img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.recipe .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #144A17;
  color: White;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
}

button {
  height: 50px;
  background: #CDA12E;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>
