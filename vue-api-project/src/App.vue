<script>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
      <nav>
        <RouterLink to="/">Leading Causes of Death</RouterLink>
        <RouterLink to="/pie">Deaths Based on Diseases</RouterLink>
        <RouterLink to="/scatter">Amount vs. Rate</RouterLink>
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
  background-color: #8dadee;
  display: flex;
  padding: 0.8rem;
  justify-content: space-between;
  align-items: center;
  color: #17386d;
  filter: drop-shadow(0px 20px 40px #83a4e6);
}

nav a {
  padding: 0 1.5rem;
  text-decoration: none;
  color: #17386d;
  font-size: 18px;
  position: relative;
  user-select: none;
  font-size: 20px;
  cursor: pointer;
  margin: 0 20px;
}

nav a.router-link-exact-active {
  font-weight: bold;
  color: rgb(6, 58, 172);
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




