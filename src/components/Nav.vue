<template>
  <header>
    <nav>
      <div>
        <h1>crowdfund</h1>
      </div>
      <div class="nav_header">
        <ul class="nav_link">
          <li><a href="#">About</a></li>
          <li><a href="#">Discover</a></li>
          <li><a href="#">Get Started</a></li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="sass">

header
  padding: 2% 5%
  height: 320px
  background-image: url("../assets/image-hero-desktop.jpg")
  background-repeat: no-repeat
  nav
    display: flex
    align-items: center
    justify-content: space-between
    color: white
    width: 100%
    .nav_header
      width: 100%
      display: flex
      justify-content: end
    .nav_link
      display: flex
      justify-content: center
      align-items: center
      list-style-type: none
      width: 40%
      li
        margin: 0 5%
        a
          color: white
          text-decoration: none
</style>