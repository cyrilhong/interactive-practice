<template>
  <div id="app">
    <div class="hopper" :class="hopper?'hoper-active':''">
      <div class="header">
        <h1>DEVICES</h1>
      </div>
      <div class="list">
        <div class="item">
          <img src="https://img.icons8.com/ios/96/000000/computer.png">
          <span>DESKTOP</span>
        </div>
        <div class="item">
          <img src="https://img.icons8.com/wired/96/000000/visual-game-boy.png">
          <span>GAMEBOY</span>
        </div>
        <div class="item">
          <img src="https://img.icons8.com/material-outlined/96/000000/iphone.png">
          <span>MOBILE PHONE</span>
        </div>
      </div>
      <div class="photo">
        <img src="https://images.unsplash.com/photo-1483388147740-e5c70536042e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80" alt="">
      </div>
    </div>
    <full-page ref="fullpage" :options="options" id="fullpage">
      <div class="section" :class="currentTab?'openTab':''" @click="openTab(currentTab)">
        <h1>IT'S HOT TODAY</h1>
        <h2>6 DEVICES</h2>
        <div class="menu">
          <div class="item" @click="hopper=!hopper">
            <img src="https://img.icons8.com/ios/96/ffffff/computer.png">
            <span>DESKTOP</span>
          </div>
          <div class="item">
            <img src="https://img.icons8.com/wired/96/ffffff/visual-game-boy.png">
            <span>GAMEBOY</span>
          </div>
          <div class="item">
            <img src="https://img.icons8.com/material-outlined/96/ffffff/iphone.png">
            <span>MOBILE PHONE</span>
          </div>
        </div>
        <img
          class="big-img"
          src="https://images.unsplash.com/photo-1551730458-be400bef0161?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
          alt="img"
        >
        <!-- <button class="next" @click="$refs.fullpage.api.moveSectionDown()">Next</button> -->
      </div>
      <div class="section">
        <h1>WHEN GOING OUT</h1>
        <h2>4 DEVICES</h2>
        <img
          class="big-img"
          src="https://images.unsplash.com/photo-1551074659-f12c57f205b4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=80"
          alt
        >
        <button class="prev" @click="$refs.fullpage.api.moveSectionUp()">Prev</button>
      </div>
    </full-page>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {},
  methods: {
    openTab(val) {
      if (!val) {
        // console.log("open tab");
        this.currentTab = !this.currentTab;
      }
    }
  },
  data() {
    return {
      options: {
        menu: "#menu",
        anchors: ["page1", "page2"],
        sectionsColor: ["#263646", "#263646", "#263646"]
      },
      currentTab: false,
      hopper: false
    };
  }
};
</script>

<style lang="scss" scoped>
#app {
  font-family: "Avenir";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  transition: all .6s;
  transition-property: all;
  transition-timing-function: ease;
  color: #263646;
}
.section {
  position: relative;
  .big-img {
    width: 100vw;
    height: 100%;
    // top: 0;
    object-fit: cover;
    // margin-top: -240px;
    z-index: 0;
    position: absolute;
    transition: all .6s;
    object-position: 100% 100%;
    bottom: 0;
    // bottom: 100%;
  }
  h1 {
    width: 600px;
    line-height: 0.9;
    position: relative;
    z-index: 1;
    font-size: 8rem;
    padding: 100px 0 0 100px;
    margin: 0;
    transition: all .6s;
  }
  h2 {
    position: relative;
    z-index: 1;
    font-size: 3rem;
    font-weight: bold;
    margin: 0 100px;
    transition: all .6s;
  }
  ul {
    padding: 0;
    margin: 0;
  }
  ul > li {
    list-style: none;
  }
  .menu {
    display: none;
    margin: 100px;
    border-top: 1px solid #fff;
    padding-top: 40px;
    .item {
      display: inline-block;
      color: #fff;
      width: 96px;
      vertical-align: top;
      text-align: center;
      margin-right: 12px;
      cursor: pointer;
      img {
        display: inline-block;
      }
      span {
        display: inline-block;
        text-align: center;
        font-weight: bold;
      }
    }
  }
}
.openTab {
  h1,
  h2 {
    color: #fff;
    transition: all .6s;
  }
  h1 {
    font-size: 2rem;
  }
  h2 {
    font-size: 1.6rem;
  }
  .big-img {
    height: 300px;
    bottom: 0;
    top: initial;
    transition: all .6s;
    object-position: 100% 30%;
  }
  .menu {
    display: block;
  }
}

.hopper {
  right: -100vw;
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
  background-color: #fff;
  transition: all .6s;
  .header{
    padding: 20px;
  }
  .list {
    padding: 20px;
    .item {
      display: inline-block;
      width: 96px;
      text-align: center;
      vertical-align: top;
      margin-right: 20px;
    }
  }
  .photo{
    width: 100%;
    height: 600px;
    position: absolute;
    bottom: 0;
  }
}
.hoper-active {
  right: 0;
  transition: all .6s;
}
</style>
