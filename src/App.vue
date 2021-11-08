<template>
  <!-- <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div> -->
  <div id="index">
    <div id="side">
      <Side />
    </div>
    <div id="header">
      <div class="filter">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M22.5 6H19.425C19.05 4.275 17.55 3 15.75 3C13.95 3 12.45 4.275 12.075 6H1.5V7.5H12.075C12.45 9.225 13.95 10.5 15.75 10.5C17.55 10.5 19.05 9.225 19.425 7.5H22.5V6ZM15.75 9C14.475 9 13.5 8.025 13.5 6.75C13.5 5.475 14.475 4.5 15.75 4.5C17.025 4.5 18 5.475 18 6.75C18 8.025 17.025 9 15.75 9Z" fill="#3FB195"/>
          <path d="M1.5 18H4.575C4.95 19.725 6.45 21 8.25 21C10.05 21 11.55 19.725 11.925 18H22.5V16.5H11.925C11.55 14.775 10.05 13.5 8.25 13.5C6.45 13.5 4.95 14.775 4.575 16.5H1.5V18ZM8.25 15C9.525 15 10.5 15.975 10.5 17.25C10.5 18.525 9.525 19.5 8.25 19.5C6.975 19.5 6 18.525 6 17.25C6 15.975 6.975 15 8.25 15Z" fill="#3FB195"/>
        </svg>
      </div>
      <img src="./assets/logo.svg" alt="Travel Logo" class="logo">
    </div>
    <router-view class="content"/>
    <Footer id="footer">
      <span>TAIWAN TRAVEL</span>
    </Footer>
  </div>
</template>

<script>
import Side from '@/components/Side.vue'

export default {
  components: {
    Side
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

#index {
  width: 100vw;
  background: #F4F4F4;
  display: grid;
  grid-template-areas:
    "header"
    "main"
    "footer";
  grid-template-columns: 100%;

  @media(min-width: 769px) {
    grid-template-columns: 354px 1fr;
    grid-template-rows: auto 36px;
    grid-template-areas:
      "side main"
      "side footer";

  }
}

#side {
  grid-area: side;
  display: none;
  height: 100vh;
  background: #fff;
  box-shadow: 0px 14px 24px rgba(0, 0, 0, 0.04);
  @media(min-width: 769px) {
    display: block;
  }
}

#header {
  grid-area: header;
  position: relative;
  display: flex;
  align-items: center;
  height: 56px;
  width: calc(100% - 32px);
  background: #fff;
  box-shadow: 0px 1px 0px rgba(0,0,0,.08);
  padding: 0 16px;

  @media(min-width: 769px) {
    display: none;
  }

  .filter {
    width: 32px;
    height: 32px;
    background: rgba(63, 177, 149, 0.08);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;

    &:hover svg path{
      fill: rgba(0, 0, 0, 0.38);
    }
  }

  .logo {
    position: absolute;
    width: 260px;
    height: 40px;
    top:50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}

.content {
  grid-area: main;
  min-height: calc(100vh - 92px);
}

#footer {
  grid-area: footer;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #3FB195;
  color: #FFF;
}
</style>
