<template>
  <section>
    <div class="section2">
      <div class="resume">
        <div class="collected">
          <h1>$89,914</h1>
          <span>of $100,000 backed</span>
        </div>
        <div class="bar"></div>
        <div class="backers">
          <h1>5,007</h1>
          <span>total backers</span>
        </div>
        <div class="days">
          <h1>56</h1>
          <span>days left</span>
        </div>
      </div>
      <div class="progress">
        <div></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>

.section2
  background-color: white
  display: flex
  flex-direction: column
  justify-content: center
  align-items: center
  border-radius: 10px
  padding: 5%
  width: 45vw
  transform: translateY(-40%)
  .resume
    width: 100%
    display: flex
    justify-content: space-evenly
    margin-bottom: 20px
  .bar
    width: 1px
    height: 60px
    background-color: lightgray
    margin: auto 5px
  .collected, .backers, .days
    display: flex
    flex-direction: column
    justify-content: flex-end
    align-items: flex-start
    width: 33%
    h1
      margin-bottom: 0
    span
      color: grey
  .progress
    width: 100%
    border-radius: 30px
    overflow: hidden
    background-color: lightgray
    div
      height: 20px
      width: 80%
      background-color: hsl(176, 50%, 47%)
      border-radius: 30px

</style>