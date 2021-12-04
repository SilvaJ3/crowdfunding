<template>
  <div class="pledgeModal">
    <div>
      <h1>Back this project</h1>
      <img src="../assets/icon-close-modal.svg" alt="" @click="() => this.$emit('closeModal')">
    </div>
    <p>Want to support us in bringing Mastercraft Bamboo Monitor Riser out in the world?</p>
    <div class="gridPledge">
      <form @submit.prevent>
        <!-- No Reward -->
        <div class="optionPledge" :class="selected_pledge_one ? 'active' : ''">
          <div class="headingPledge">
            <div class="radio-item">
              <input type="radio" name="option1" :checked="selected_pledge_one === true ? 'checked' : ''" class="input_no_reward">
              <label for="option1" @click="selected_pledge_one = !selected_pledge_one">
                <h2>Pledge with no reward</h2>
                <p>Choose to support us without a reward if you simply believe in our project. As a backer, you will be signed up to receive product updates via email.</p>
              </label>
            </div>
          </div>
          
          <template v-if="selected_pledge_one">
            <div class="footerPledge">
              <hr>
              <div>
                <div class="enterPledgePart">
                  <div>
                    <p>Enter your pledge</p>
                  </div>
                  <div class="buttonsPledge">
                    <input type="text" step="1" v-model="pledgeValue">
                    <div class="continueBtn" @click="confirmPledge(null)">
                      <span>Continue</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </template>
        </div>

        <!-- V-for Pledge -->
        <div class="optionPledge" :class="pledge.selected ? 'active' : ''" v-for="(pledge, index) in pledges" :key="'modal' + index">
          <div class="headingPledge">
            <div class="radio-item">
              <input type="radio" :name="'pledge'+(index + 1)" :checked="pledge.selected === true ? 'checked' : ''">
              <label :for="'pledge'+(index + 1)" @click="selectPledge(pledge.left, pledge)">
                <div class="top_heading_pledge">
                  <div class="pledge_title">
                    <h2>{{ pledge.title }}</h2>
                    <p>{{ pledge.pledge }}</p>
                  </div>
                  <h1>{{ pledge.left }} <span>left</span></h1>
                </div>
                <p>{{ pledge.description }}</p>
              </label>
            </div>
          </div>
          
          <template v-if="pledge.selected">
            <div class="footerPledge">
              <hr>
              <div>
                <div class="enterPledgePart">
                  <div>
                    <p>Enter your pledge</p>
                  </div>
                  <div class="buttonsPledge">
                    <input type="text" step="1" v-model="pledgeValue">
                    <div class="continueBtn" @click="confirmPledge(index)">
                      <span>Continue</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </template>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      selected_pledge_one: false,
      pledgeValue: 0
    }
  },
  props: {
    pledges: Array
  },
  methods: {
    selectPledge(left, pledge){
      if(left > 0) {
        pledge.selected = !pledge.selected;
      }
    },
    confirmPledge(index){
      if (this.pledgeValue == 0) {
        this.pledgeValue = this.pledges[index].value;
      }
      this.$emit("pledgeSelected", this.pledgeValue);
      this.pledgeValue = 0;
    }
  },
}
</script>

<style lang="sass">
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
  img
    cursor: pointer
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
    margin-top: 3%
    h2
      cursor: pointer
  .active
    border: solid 2px hsl(176, 50%, 47%) !important
  .headingPledge
    padding: 5%
    .radio-item
      display: flex !important
      align-items: start !important
      .input_no_reward
        margin-top: -2% !important
        margin-right: 5%
        height: 40px
        width: 40px
      input
        margin-top: 11px
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
      .top_heading_pledge
        display: flex
        justify-content: space-between
        align-items: center
        .pledge_title
          width: 80%
          display: flex
          justify-content: start
        h2
          margin: 0 4% 0 0
        p
          font-size: 14px
          font-weight: 700
          color: hsl(176, 50%, 47%)
        h1
          font-size: 25px
          display: flex
          align-items: center
          span
            margin-left: 5px
            font-size: 14px
            color: grey
            font-weight: normal
  .footerPledge
    width: 100%
    .enterPledgePart
      padding: 2% 5%
    .buttonsPledge
      display: flex
      justify-content: space-between
      width: 35%
      input
        border-radius: 30px
        border: solid 1px hsl(176, 50%, 47%)
        width: 70px
        height: 30px
        text-align: center
        background-image: url("../assets/icon-dollar.svg")
        background-repeat: no-repeat
        background-position-x: 20%
        background-position-y: 50%
      .continueBtn
        background-color: hsl(176, 50%, 47%)
        width: 70px
        padding: 3% 4%
        border-radius: 30px
        display: flex
        align-items: center
        justify-content: center
        color: white
        font-size: 12px
        cursor: pointer
      .continueBtn:hover
        background-color: #157a72
</style>