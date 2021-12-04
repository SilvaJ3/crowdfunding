<template>
  <section>
    <div class="section3">
      <h1>{{ title }}</h1>
      <p class="about">{{about_part1}}</p>
      <p class="about">{{about_part2}}</p>

      <div class="pledge">

        <!-- OPTION -->

        <div class="option" v-for="(pledge, index) in pledges" :key="'option_' + index" :class="pledge.left === 0 ? 'outOfStock' : ''">
          <div class="heading_option">
            <h1>{{ pledge.title }}</h1>
            <p>{{ pledge.pledge }}</p>
          </div>
          <div class="description">
            <p>{{ pledge.description }}</p>
          </div>
          <div class="footer_option">
            <h1>{{ pledge.left }} <span>left</span></h1>
            <div class="selectReward">
              <span>{{ pledge.left > 0 ? "Select Reward" : "Out of stock"}}</span>
            </div>
          </div>
        </div>

        
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data(){
    return {
      title: "About this project",
      about_part1: "The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform that elevates your screen to a more comfortable viewing height. Placing your monitor at eye level has the potential to improve your posture and make you more comfortable while at work, helping you stay focused on the task at hand.",
      about_part2: "Featuring artisan craftsmanship, the simplicity of design creates extra desk space below your computer to allow notepads, pens, and USB sticks to be stored under the stand.",
    }
  },
  props: { 
    pledges: Array,
    }
}
</script>

<style lang="sass">
.section3
  background-color: white
  display: flex
  flex-direction: column
  justify-content: center
  border-radius: 10px
  padding: 5%
  width: 45vw
  transform: translateY(-10%)
  border: solid 1px lightgray
  .about
    color: grey
  .pledge
    margin-top: 4%
    display: grid
    grid-template-row: repeat(3, 45vw)
    .option
      display: flex
      flex-direction: column
      border: solid 2px lightgray
      border-radius: 15px
      padding: 3% 4%
      margin-bottom: 4%
      .heading_option
        display: flex
        justify-content: space-between
        align-items: center
        h1
          font-size: 18px
        p
          font-size: 14px
          font-weight: 700
          color: hsl(176, 50%, 47%)
      .description
        p
          color: grey
          line-height: 2
      .footer_option
        display: flex
        justify-content: space-between
        align-items: center
        h1
          font-size: 25px
          display: flex
          align-items: center
          span
            margin-left: 5px
            font-size: 14px
            color: grey
            font-weight: normal
        .selectReward
          background-color: hsl(176, 50%, 47%)
          border-radius: 30px
          color: white
          cursor: pointer
          padding: 2% 4%
          font-size: 13px
        .selectReward:hover
          background-color: #157a72
    .outOfStock
      opacity: 0.4
      .selectReward
        background-color: gray !important
        cursor: default !important

</style>