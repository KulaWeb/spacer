<template>
  <div class="app">
    <div class="nav">
      <router-link to="/">Spacer</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">

  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800&display=swap');

  * {
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
    color: #fff;
  }
  .app {
    .nav {
      position: fixed;
      background-color: rgba(255,255,255, .6);
      width: 100%;
      height: 50px;
      display: flex;
      align-items: center;
      a {
        color: #333;
        font-size: 17px;
        letter-spacing: 1px;
        padding: 10px;
        &:last-of-type {
          text-align: right;
        }
      }
    }
  }

</style>
