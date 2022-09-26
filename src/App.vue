<template>
  <div id="app">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
* {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: "Montserrat", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  color: #000;
}

html {
  scroll-behavior: smooth;
}
::-webkit-scrollbar {
  width: 7px;
}

::-webkit-scrollbar-thumb {
  background: #ececec;
  border-radius: 6px;
  height: 55px;
}
a {
  text-decoration: none;
}
img {
  max-width: 100%;
  display: block;
}

[data-anima="top"] {
  animation: showTop 0.5s forwards;
}
@keyframes showTop {
  from {
    opacity: 0;
    transform: translate3d(0, -20px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
[data-anima="bottom"] {
  animation: showBottom 0.5s forwards;
}
@keyframes showBottom {
  from {
    opacity: 0;
    transform: translate3d(0, 20px, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
[data-anima="left"] {
  animation: showLeft 0.5s forwards;
}
@keyframes showLeft {
  from {
    opacity: 0;
    transform: translate3d(-20px, 0, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
[data-anima="right"] {
  animation: showRight 0.5s forwards;
}
@keyframes showRight {
  from {
    opacity: 0;
    transform: translate3d(20px, 0, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}
.container {
  max-width: 1250px;
  margin: 0 auto;
  padding: 0 10px;
}

#app {
  display: flex;
  min-height: 105vh;
  flex-direction: column;
}

#main {
  flex: 1;
}
.btn {
  display: block;
  font-family: "Montserrat", sans-serif;
  background: #000;
  color: #fff;
  font-weight: 600;
  font-size: 14px;
  padding: 10px 25px;
  border: none;
  cursor: pointer;
  transition: 0.3s !important;
  height: 55px;
  border-radius: 5px;
}

input {
  border-radius: 5px;
  border: 1px solid #ededf0;
  padding: 15px;
  height: 55px;
  transition: 0.3s;
  font-size: 15px;
  font-family: "Montserrat", sans-serif;
  margin-bottom: 20px;
  width: 100%;
  resize: none;
  /* background: #f7f7f7; */
}

input:hover {
  outline: none;
  border-color: #000;
}

input::placeholder {
  font-size: 14px;
}
</style>
