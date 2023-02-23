<script setup></script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light p-3">
      <a href="" class="navbar-brand">
        <img src="../assets/Vue_Logo_Black.png" alt="Todo" />
        <span>Vue Tasks</span>
      </a>

      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <RouterLink class="nav-link text-decoration-none" to="/"
            >Home</RouterLink
          >
        </li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
nav {
  img {
    width: 32px;
  }
  span {
    font-weight: 500;
  }
}
</style>
