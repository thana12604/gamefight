<template>
<div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <Game />
</div>
</template>

<script>
import Game from './components/Game'
export default {
    name: 'App',
    components: {
        Game
    }
}
</script>

<style>
#app {
    font-family: 'Russo One', sans-serif;
    font-size: 24px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    margin-top: 60px;
}
body {
    background-image: url("https://i.pinimg.com/originals/36/43/2e/36432efea95d385a3495f56b434daa96.gif");
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>