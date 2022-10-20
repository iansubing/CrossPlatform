<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <button class="btn btn-danger navbar-btn">Home</button>
        </li>
        <li class="nav-item">
          <NuxtLink to="/dashboard" class="btn btn-danger navbar-btn">Dashboard</NuxtLink>
        </li>
        <li class="nav-item">
          <button class="btn btn-danger navbar-btn">Register</button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>