<script>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
      <nav>
        <RouterLink to="/">Bar Chart</RouterLink>
        <RouterLink to="/pie">Pie Chart</RouterLink>
        <RouterLink to="/scatter">Scatter Chart</RouterLink>
      </nav>
      <img src="\skull.png" alt="skull">
      <h1>Leading Causes of Deaths in NYC</h1>
  </header>
  <RouterView/>
</template>

<style scoped>
header {
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  background-color: rgb(152, 212, 144);
  display: flex;
  padding: 0.8rem;
  justify-content: space-between;
  align-items: center;
}

nav {
  display: flex;
}

nav a {
  padding: 0 1.5rem;
  text-decoration: none;
  color: var(--color-text);
}

nav a.router-link-exact-active {
  font-weight: bold;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}
h1 {
  text-align: right;
  font-size: 29px;
  margin-right: 1rem;
}
img {
  width: 2.5%;
  margin-left: auto;
  margin-right: 1.3rem;
}
</style>




