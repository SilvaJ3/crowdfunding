<template>
  <section>
    <div class="heading">
      <div class="logo">
        <img :src="logo" alt="">
      </div>
      <h1>{{ title }}</h1>
      <p>{{ subtitle }}</p>
      <div class="buttons">
        <div class="supportProjectBtn">
          <span>{{ button }}</span>
        </div>
        <div class="bookmark">
          <img :src="bookmarkIcon" alt="">
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
      logo: logo
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
        padding: 2% 8%
        background-color: hsl(176, 50%, 47%)
        color: white
        text-align: center
      .bookmark
        display: flex
        justify-content: center
        align-items: center
        img
          margin-right: 10%
    .logo
      position: absolute
      top: -12%
      margin: 0
      padding: 0
</style>