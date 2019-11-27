<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/interactive-paycard">响应式的信用卡</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
body {
  background-color: #ddeefc;
  font-size: 16px;
}

* {
  box-sizing: border-box;
  &:focus {
    outline: none;
  }
}
</style>
