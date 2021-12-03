<template>
  <div id="app">
    <Nav />
    <div class="section">
      <Dashboard />
      <Resume />
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav.vue"
import Dashboard from "./components/Dashboard.vue"
import Resume from "./components/Resume.vue"

export default {
  name: 'App',
  components: { Nav, Dashboard, Resume }
}
</script>

<style lang="sass">
body
  padding: 0
  margin: 0
  box-sizing: border-box
  font-family: 'Commissioner', sans-serif

#app
  display: flex
  flex-direction: column
  justify-content: center
  .section
    padding: auto 20%
    background-color: hsl(176, 50%, 47%)
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center

</style>
