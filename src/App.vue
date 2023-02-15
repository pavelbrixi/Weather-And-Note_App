<template>
  <header>
    <div class="logo">
      <img src="./assets/logo.png" alt="logo">
      <p>Pavel Brixí - pololetní práce</p>
    </div>
    <nav>
      <router-link to="/">Počasí</router-link> |
      <router-link to="/about">Úkolníček</router-link>
    </nav>
  </header>
  
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  display: flex;
  justify-content: space-between;
  height: 10vh;
  background-color: #FFF;
  box-shadow: 100cm;
}

nav {
  padding: 30px;
}

.logo {
  display: flex;
  align-items: center;
  padding: 2.5vh;
  
}

p {
  font-weight: bold;
  font-size: large;
}

img {
  width: 8vh;
  aspect-ratio: 3/2;
  object-fit: contain;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
