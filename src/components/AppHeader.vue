<script setup lang="ts"></script>

<template>
  <header>
    <BNavbar toggleable="lg" variant="info" v-b-color-mode="'light'" :container="true" fixed="top">
      <BNavbarBrand to="/">NavBar</BNavbarBrand>
      <BNavbarToggle target="nav-collapse" />
      <BCollapse id="nav-collapse" is-nav>
        <!-- Right aligned nav items -->
        <BNavbarNav class="ms-auto mb-2 mb-lg-0">
          <BNavItem to="/">Home</BNavItem>
          <BNavItem to="/about">About</BNavItem>
          <BNavItem to="/register">Register</BNavItem>
          <BNavItem to="/login">Login</BNavItem>
        </BNavbarNav>
        <BNavForm class="d-flex">
          <BFormInput class="me-2" placeholder="Search" />
          <BButton type="submit" variant="outline-light">Search</BButton>
        </BNavForm>
      </BCollapse>
    </BNavbar>
  </header>
</template>

<style scoped></style>
