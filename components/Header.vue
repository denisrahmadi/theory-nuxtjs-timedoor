<template>
  <div>
    <header class="header">
      <nuxt-link 
        tag="a" 
        class="navbar-brand text-brand" 
        to="/"
      >
        <img
          src="/images/logo.png"
          alt="Logo"
          width="44"
          height="44"
          class="d-inline-block align-text-center"
        />
        Food Recipes
      </nuxt-link>
      <nav class="header-nav">
        <nuxt-link to="/" class="header-nav__link">Home</nuxt-link>
        <nuxt-link to="/add" class="header-nav__link"> Add Recipes </nuxt-link>
        <nuxt-link
          tag="a"
          to="/user/login"
          class="header-nav__link"
          v-if="!$store.getters.isAuthenticated"
        >
          Login
        </nuxt-link>
        <a
          class="header-nav__link"
          v-if="$store.getters.isAuthenticated"
          @click="logout"
        >
          Logout
        </a>
        <nuxt-link
          tag="a"
          to="/user"
          class="header-nav__link"
          v-if="$store.getters.isAuthenticated"
        >
          {{ $store.state.userData.username }}
        </nuxt-link>
      </nav>
    </header>
  </div>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$router.push("/user/login");
    },
  },
};
</script>

<style scoped>
body {
  margin: 0px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 40px;
  padding-right: 40px;
  background-color: #eef2e6;
}
.text-brand{
  font-family: 'Satisfy', cursive;
}

main {
  margin: 22px;
}

.recipes {
  display: flex;
  flex-wrap: wrap;
}

.header-nav__link {
  margin-left: 20px;
  color: black;
  text-decoration: none;
  font-size: 20px;
}

/* Recipe Content */
.recipes-content {
  background-color: #eef2e6;
  padding: 10px;
  margin: 13px 13px;
}

.recipes-content__body {
  padding: 5px;
}

.recipes-content__img {
  width: 280px;
  height: 210px;
}

.recipes-content__body__review {
  display: flex;
  align-items: center;
}

.recipes-content__body__review img {
  width: 20px;
  height: 20px;
  margin: 5px 10px 5px 0px;
}

.recipes-content__body__review p {
  margin: 0px;
}

.recipes-content__body__review img:hover {
  cursor: pointer;
}

.recipes-content__body__title {
  margin: 5px 0px;
}

/* Add Recipe */
.add-recipe__title,
.add-recipe__desc {
  display: block;
  width: 100%;
  margin: 10px 0px;
  border: none;
}

.add-recipe__title {
  height: 50px;
  font-size: 25px;
}

.add-recipe__desc {
  height: 300px;
}

.add-recipe__img {
  border: none;
  height: 30px;
}

.add-recipe__button {
  color: white;
  background-color: #4b56d2;
  border: none;
  padding: 20px;
  border-radius: 15px;
  font-weight: bold;
}

.add-recipe__button:hover {
  cursor: pointer;
  background-color: #82c3ec;
  color: #4b56d2;
}

/* Detail */
.recipes-detail {
  display: flex;
  justify-content: center;
}

.recipes-detail div {
  width: 600px;
}

.recipes-detail__img {
  width: 400px;
  height: 300px;
  display: block;
  text-align: center;
  margin: 0px auto;
}

.recipes-detail__title {
  text-align: center;
}
</style>
