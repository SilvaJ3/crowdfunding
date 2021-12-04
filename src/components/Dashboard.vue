<template>
  <section>
    <div class="heading">
      <div class="logo">
        <img :src="logo" alt="">
      </div>
      <h1>{{ title }}</h1>
      <p>{{ subtitle }}</p>
      <div class="buttons">
        <div class="supportProjectBtn" @click="() => this.$emit('openModal')">
          <span>{{ button }}</span>
        </div>
        <div class="bookmark" @click="bookmarked = !bookmarked" :class="bookmarked ? 'bookmarked' : ''">
          <div class="icon">
            <i class="fas fa-bookmark"></i>
          </div>
          <p>{{ bookmark }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import bookmarkIcon from "../assets/icon-bookmark.svg";
import logo from "../assets/logo-mastercraft.svg";


export default {
  data(){
    return {
      title: "Mastercraft Bamboo Monitor Riser",
      subtitle: "A beautiful & handcrafted monitor stand to reduce neck and eye strain.",
      button: "Back this project",
      bookmark: "Bookmark",
      bookmarkIcon: bookmarkIcon,
      logo: logo,
      bookmarked: false
    }
  }
}
</script>

<style lang="sass">
  .heading
    border-radius: 10px
    background-color: white
    position: relative
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
    padding: 5%
    width: 45vw
    transform: translateY(-40%)
    h1
      margin-bottom: 0
    p
      font-weight: 400
      color: grey
    .buttons
      display: flex
      justify-content: space-between
      align-items: center
      width: 100%
      margin-top: 3%
      .supportProjectBtn
        border-radius: 30px
        padding: 17px 30px
        background-color: hsl(176, 50%, 47%)
        color: white
        text-align: center
        cursor: pointer
        span
          pointer-events: none
      .supportProjectBtn:hover
        background-color: #157a72
      .bookmark
        display: flex
        align-items: center
        border-radius: 30px
        background-color: #f4f4f4
        width: 160px
        cursor: pointer
        .icon
          margin-right: 10%
          width: 50px
          height: 50px
          background-color: #2f2f2f
          color: #b1b1b1
          border-radius: 50%
          display: flex
          justify-content: center
          align-items: center
        p
          font-weight: 700
      .bookmarked
        p
          color: hsl(176, 50%, 47%)
        .icon
          background-color: hsl(176, 50%, 47%) 
          color: white
      .bookmark:hover
        opacity: 0.75
    .logo
      position: absolute
      top: -12%
      margin: 0
      padding: 0
</style>