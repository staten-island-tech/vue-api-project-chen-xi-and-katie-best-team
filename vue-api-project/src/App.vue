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
  </header>
  <RouterView/>
</template>

<style scoped>
header {
  position: fixed;
  width: 100%;
  left: 0;
  background-color: rgb(152, 212, 144);
  display: flex;
  justify-content: flex-start;
  padding: 1rem;
}

nav {
  display: flex;
}

nav a {
  padding: 0 1rem;
  text-decoration: none;
  color: var(--color-text);
}

nav a.router-link-exact-active {
  font-weight: bold;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}
</style>



