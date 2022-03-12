<template>
<div>
  <div v-if="this.$root.$data.cart.length > 0">
    <CartList :recipes="recipes" />
  </div>
  <div v-else>
    <p>No Recipes Added... Aren't you hungry?</p>
  </div>
  <footer>
    <p><a href="https://github.com/emiblackk/cp3.git">Repo</a></p>
  </footer>
</div>
</template>

<script>
import CartList from "../components/CartList.vue"
export default {
  name: 'Cart-view',
  components: {
    CartList
  },
  data() {
    return {
      searchText: '',
    }
  },
  computed: {
    recipes() {
      return this.$root.$data.cart;
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

p {
  text-align: center;
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
