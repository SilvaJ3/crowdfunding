<template>
  <div id="app">
    <div v-show="showModal" class="backdrop">
      <ModalSelect v-show="showPledgeModal" :pledges="pledges_update" @closeModal="closeModal" @pledgeSelected="pledgeSelected"/>
      <ModalConfirm v-show="showConfirmModal" @closeModal="closeModal"/>
    </div>
    <Nav />
    <div class="section">
      <Dashboard @openModal="openModal"/>
      <Resume :crowdfunding="crowdfunding_update"/>
      <PledgeBox :pledges="pledges_update" @openSelectedModal="openSelectedModal"/>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav.vue"
import Dashboard from "./components/Dashboard.vue"
import Resume from "./components/Resume.vue"
import PledgeBox from "./components/PledgeBox.vue"
import ModalSelect from "./components/ModalSelect.vue"
import ModalConfirm from "./components/ModalConfirm.vue"

export default {
  name: 'App',
  components: { Nav, Dashboard, Resume, PledgeBox, ModalSelect, ModalConfirm },
  data(){
    return {
      pledges: [
        {
          title: "Bamboo Stand",
          pledge: "Pledge $25 or more",
          description: "You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you’ll be added to a special Backer member list.",
          left: 101,
          value: 25,
          selected: false,
        },
        {
          title: "Black Edition Stand",
          pledge: "Pledge $75 or more",
          description: "You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          left: 64,
          value: 75,
          selected: false,
        },
        {
          title: "Mahogany Special Edition",
          pledge: "Pledge $200 or more",
          description: "You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          left: 0,
          value: 200,
          selected: false,
        }
      ],
      crowdfunding: {
        goal: 100000,
        total: 89914,
        backers: 5007,
        daysLeft: 56,
      },
      crowdfunders: [],
      showModal: false,
      showPledgeModal: false,
      showConfirmModal: false,
    }
  },
  methods: {
    closeModal() {
      this.showModal = false;
      this.showPledgeModal = false;
      this.showConfirmModal = false;
    },
    openModal() {
      this.showModal = true;
      this.showPledgeModal = true;
    },
    openSelectedModal(index) {
      this.showModal = true;
      this.showPledgeModal = true;
      this.pledges[index].selected = true;
    },
    pledgeSelected(value, index) {
      let crowfunder = {
        pledge: this.pledges[index],
        amount: value,
      }
      this.crowdfunders.push(crowfunder);
    },
    updateTotal(){
      this.crowdfunders.forEach(element => {
        this.crowdfunding.backers++;
        this.crowdfunding.total = parseFloat(this.crowdfunding.total) + parseFloat(element.amount);
      })

      this.showPledgeModal = false;
      this.showConfirmModal = true;

    },
    updatePledges(){
      this.crowdfunders.forEach(element => {
        if (element.pledge) {
          let index = this.pledges.indexOf(element.pledge)
          console.log(index);
          this.pledges[index].left--;
        }
      })

      this.showPledgeModal = false;
      this.showConfirmModal = true;

    }
  },
  computed: {
    crowdfunding_update: function() {
      if(this.crowdfunders[0]) {
        this.updateTotal();
      }
      return this.crowdfunding;
    },
    pledges_update: function() {
      if(this.crowdfunders[0]) {
        this.updatePledges();
      }
      return this.pledges;
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
  .section
    padding: auto 20%
    background-color: #fafafa
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center


</style>
