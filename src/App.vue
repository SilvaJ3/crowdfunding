<template>
  <div id="app">
    <div v-show="showModal" class="backdrop">
      <div class="pledgeModal" v-show="showPledgeModal">
        <div>
          <h1>Back this project</h1>
          <img src="./assets/icon-close-modal.svg" alt="">
        </div>
        <p>Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the world?</p>
        <div class="gridPledge">
          <div class="optionPledge" @click="selected = !selected" :class="selected ? 'active' : ''">
            <div class="headingPledge">
              <div class="radio-item">
                <input type="radio" name="option1" id="">
                <label for="option1">
                  <h2>Pledge with no reward</h2>
                  <p>Choose to support us without a reward if you simply believe in our project. As a backer, you will be signed up to receive product updates via email.</p>
                </label>
              </div>
            </div>
            
            <template v-if="selected">
              <div class="footerPledge">
                <div class="enterPledgePart">
                  <div>
                    <p>Enter your pledge</p>
                  </div>
                  <div class="buttonsPledge">
                    <input type="text" step="1">
                  </div>
                </div>
              </div>
            </template>
          </div>
        </div>
      </div>
    </div>
    <Nav />
    <div class="section">
      <Dashboard />
      <Resume />
      <PledgeBox :pledges="pledges"/>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav.vue"
import Dashboard from "./components/Dashboard.vue"
import Resume from "./components/Resume.vue"
import PledgeBox from "./components/PledgeBox.vue"

export default {
  name: 'App',
  components: { Nav, Dashboard, Resume, PledgeBox },
  data(){
    return {
      pledges: [
        {
          title: "Bamboo Stand",
          pledge: "Pledge $25 or more",
          description: "You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you’ll be added to a special Backer member list.",
          left: 101,
        },
        {
          title: "Black Edition Stand",
          pledge: "Pledge $75 or more",
          description: "You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          left: 64,
        },
        {
          title: "Mahogany Special Edition",
          pledge: "Pledge $200 or more",
          description: "You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          left: 0,
        }
      ],
      showModal: true,
      showPledgeModal: true,
      selected: true
    }
  }
}
</script>

<style lang="sass">
body
  padding: 0
  margin: 0
  box-sizing: border-box
  font-family: 'Commissioner', sans-serif
  position: relative
#app
  display: flex
  flex-direction: column
  justify-content: center
  .backdrop
    height: 100%
    width: 100%
    z-index: 2
    position: absolute
    top: 0
    left: 0
    background-color: rgba(0, 0, 0, 0.5)
  .pledgeModal
    position: absolute
    top: 9%
    left: 27%
    width: 40vw
    background-color: white
    border-radius: 15px
    padding: 5%
    display: flex
    flex-direction: column 
    div:nth-child(1)
      display: flex
      justify-content: space-between
      align-items: center
      h1
        font-size: 23px
    p
      color: grey
      font-size: 15px
    // .gridPledge
    //   display: grid
    //   grid-template-rows: repeat(4, 30vw)
    .optionPledge
      border-radius: 15px
      border: solid 1px lightgrey
      display: flex
      flex-direction: column
    .active
      border: solid 2px hsl(176, 50%, 47%) !important
    .headingPledge
      padding: 5%
      .radio-item
        display: flex !important
        align-items: start !important
        input
          margin-top: -2%
          margin-right: 5%
          height: 40px
          width: 40px
        input:checked
          background-color: hsl(176, 50%, 47%)
        h2
          font-size: 15px
          margin-top: 0
        h2:hover
          color: hsl(176, 50%, 47%)
        p
          font-size: 13px
    .footerPledge
      width: 100%
      .enterPledgePart
        padding: 2% 5%
      .buttonsPledge
        .input
          border-radius: 30px
  .section
    padding: auto 20%
    background-color: #fafafa
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center


</style>
