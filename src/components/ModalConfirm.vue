<template>
  <div class="confirmModal">
      <img src="../assets/icon-check.svg" alt="">
      <h1>Thanks for your support</h1>
      <p>Your pledge brings us one step closer to sharing Mastercraft Bamboo Monitor Riser worldwide. You will get an email once our campaign is completed.</p>
      <div class="confirmBtn" @click="() => this.$emit('closeModal')">
        <span>Got it!</span>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="sass">
.confirmModal
  position: absolute
  top: 9%
  left: 36%
  width: 25vw
  background-color: white
  border-radius: 15px
  padding: 3%
  display: flex
  flex-direction: column 
  justify-content: space-evenly
  align-items: center
  h1
    font-size: 23px
  p
    color: grey
    font-size: 15px
    text-align: center
    line-height: 2
  .confirmBtn
    cursor: pointer
    margin-top: 3%
    border-radius: 30px
    padding: 3% 5%
    background-color: hsl(176, 50%, 47%)
    span
      pointer-events: none
      color: white
  .confirmBtn:hover
    background-color: #157a72

  
</style>