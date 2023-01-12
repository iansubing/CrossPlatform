<template>
  <div>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <nav style="height: 50px">
      <li>
        <div>
          <b-button v-b-toggle.sidebar-1 vertical class="btn-danger d-block p-3 link-danger text-decoration-none">Menu ☰</b-button>
          <b-sidebar id="sidebar-1" title="Menu" shadow>
            <nav class="mb-3">
            <b-nav vertical>
              <NuxtLink to="/dashboard" class="btn btn-danger navbar-btn fa fa-home"> Home</NuxtLink>
              <NuxtLink to="/addstudents" class="btn btn-danger navbar-btn fa fa-user"> Add Students</NuxtLink>
            </b-nav>
          </nav>
          </b-sidebar>
        </div>
      </li>
      <li style="float:right"><a href="/" class="d-block p-3 link-danger text-decoration-none" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Icon-only">
      <svg class="bi" width="40" height="1px"><use xlink:href="#bootstrap"></use></svg>
      <span>Logout</span>
    </a></li>
    </nav>
    <h1 style="text-align: center; margin-top: 50px">Welcome to Enrollment Page</h1>
  </div>
</template>

<style scoped>
nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #ef3636;
  }

li {
    float: left;
    border-right:1px solid #bbb;
  }

li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
  }

li a:hover:not(.active) {
    background-color: #111;
  }
</style>