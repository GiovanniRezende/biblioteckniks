<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/autores">Autores</RouterLink>
      <RouterLink to="/editoras">Editoras</RouterLink>

      <img src="@\components\icons\livroicon.png" class="LivroIco" />
    </nav>
  </header>

  <RouterView />
  <div class="footer fixed-bottom">App by Bibliotecnicks</div>
</template>

<style>
@import "@/assets/base.css";
.LivroIco {
  height: 2em;
  float: right;
  margin-right: 1em;
}
.footer {
  line-height: 1.5;
  max-height: 100vh;
  padding: 1vh;
  box-shadow: 1px 1px 5px black;
  background-color: white;
}
header {
  line-height: 1.5;
  max-height: 100vh;
  margin-bottom: 2vh;
  padding: 1vh;
  box-shadow: 1px 1px 5px black;
}
a,
.green {
  text-decoration: none;
  color: rgb(173, 0, 189);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(308, 100%, 37%, 0.2);
  }
}
nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}
</style>
