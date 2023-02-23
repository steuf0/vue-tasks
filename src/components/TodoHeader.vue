<script setup></script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a href="" class="navbar-brand">
        <img src="../assets/Vue_Logo_Black.png" alt="Todo" />
        <span>Vue Tasks</span>
      </a>

      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <RouterLink to="/"><span class="nav-link">Home</span></RouterLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
nav {
  padding: 1rem;
  img {
    width: 32px;
  }
}
</style>
