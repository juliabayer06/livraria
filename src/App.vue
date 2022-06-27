<script setup></script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink> |
      <RouterLink to="/categorias">Categorias</RouterLink> |
      <RouterLink to="/editoras">Editoras</RouterLink> |
      <RouterLink to="/autores">Autores</RouterLink> |
      <RouterLink to="/livros">Livros</RouterLink> |
    </nav>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}
</style>
