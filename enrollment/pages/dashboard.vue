<template>
    <nav>
      <li><a href="#">Home</a></li>
      <li><a href="#">Courses</a></li>
      <li><a href="#">About Us</a></li>
      <li style="float:right"><NuxtLink to="/index" class="btn text-light mh-100">Logout</NuxtLink></li>
    </nav>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>

<style>
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

  li:last-child {
    border-right: none;
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