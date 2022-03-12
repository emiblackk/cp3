<template>
<div id="app">
  <div id="menu">
    <div id="brand">
      <router-link to="/">
        <img src="/images/chef.png">
      </router-link>
    </div>
    <div id="side">
      <router-link to="/cart">
        <div class="menu-item">
          <img src="/images/note.jpeg">
          <p>{{numItems}} Saved Recipes</p>
        </div>
      </router-link>
    </div>
  </div>
  <router-view />
  <RecipeList />

</div>
</template>

<script>
import RecipeList from "./components/RecipeList.vue"
export default {
  name: 'App-view',
  components: {
    RecipeList,
  },
  computed: {
    numItems() {
      return this.$root.$data.cart.length;
    }
  },
  componentDidUpdate() {
        console.log("here")
    }
}
</script>



<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;

}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}
</style>
