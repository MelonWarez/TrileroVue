<!-- <script setup lang="ts">
defineProps<{
  msg: string
}>()
</script> -->
<!-- 
<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>. What's next?
    </h3>
  </div>
</template> -->

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  /* position: relative; */
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}
/* 
@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
} */
</style>


<!--
FLIP list transitions with the built-in <TransitionGroup>.
https://aerotwist.com/blog/flip-your-animations/
-->

<script setup lang="ts">
import { shuffle as _shuffle } from 'lodash-es'
import { ref } from 'vue'
import { TransitionGroup } from 'vue';

defineProps<{
  msg: string
}>()

const getInitialItems = () => [1, 2, 3, 4, 5]
const items = ref(getInitialItems())
let id = items.value.length + 1

function insert() {
  const i = Math.round(Math.random() * items.value.length)
  items.value.splice(i, 0, id++)
}

function reset() {
  items.value = getInitialItems()
}

function shuffle() {
  items.value = _shuffle(items.value)
}

function remove(item) {
  const i = items.value.indexOf(item)
  if (i > -1) {
    items.value.splice(i, 1)
  }
}
</script>

<template>
  <div>
    <button @click="insert">insert at random index</button>
    <button @click="reset">reset</button>
    <button @click="shuffle">shuffle</button>

    <TransitionGroup tag="ul" name="fade" class="container">
      <div v-for="item in items" class="item" :key="item">
        {{ item }}
        <button @click="remove(item)">x</button>
      </div>
    </TransitionGroup>
  </div>
</template>

<style>
.container {
  position: relative;
  padding: 0;
}

.item {
  width: 10%;
  height: 30px;
  background-color: #f3f3f3;
  border: 1px solid #666;
  box-sizing: border-box;
  display: inline-block;
}

/* 1. declare transition */
.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

/* 2. declare enter from and leave to state */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}

/* 3. ensure leaving items are taken out of layout flow so that moving
      animations can be calculated correctly. */
.fade-leave-active {
  position: absolute;
}

html {
  background: url("../img/ramblas.jpg") no-repeat center center fixed;
  background-size: cover;
}

* {
  text-align: center;
}

h1 {
  color: #965705;
  font-size: 50px;
  line-height: 40px;
  font-weight: 700;
  margin: 0 5px 0;
  float: none;
  padding: 5px;
  margin: 0 5px 0;
  font-family: "Libre Baskerville", serif;
}

p {
  font-size: 40px;
  font-weight: 300;
  font-family: fantasy;
  color: rgb(255, 2, 2);
}

#gamePlace {
  position: relative;
  margin-top: 250px;
}

button {
  border: 1px solid rgba(255, 255, 255, 0.01);
  background-color: rgba(255, 255, 255, 0.01);
}

img {
  width: 100px;
  height: 130px;
}

#littleBall {
  background: rgb(9, 255, 0);
  border-radius: 50%;
  width: 20px;
  height: 20px;
  bottom: 20px;
  z-index: -1;
  position: absolute;
  -webkit-animation-duration: 8s;
          animation-duration: 8s;
  -webkit-animation-name: cupAroundDown;
          animation-name: cupAroundDown;
  transition-timing-function: ease;
}

#cups {
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  z-index: 0;
}

#cup1 {
  -webkit-animation-duration: 1.5s;
          animation-duration: 1.5s;
  -webkit-animation-name: cup1AroundDown;
          animation-name: cup1AroundDown;
}

#cup2 {
  -webkit-animation-duration: 1.5s;
          animation-duration: 1.5s;
  -webkit-animation-name: cup2AroundUpLeft;
          animation-name: cup2AroundUpLeft;
}

.cupUp {
  /* position: absolute;  */
  z-index: 0;
  -webkit-animation-duration: 1.5s;
          animation-duration: 1.5s;
  -webkit-animation-name: cupUp;
          animation-name: cupUp;
  -webkit-animation-play-state: unset;
          animation-play-state: unset;
}

#score {
  height: 100px;
  width: 300px;
  border-color: chartreuse solid 5px;
  position: relative;
  right: -80%;
  top: -10%;
  background-color: black;
  border: 5px, solid, greenyellow;
}
/* 
@-webkit-keyframes cupUp {
  0% {
    bottom: 0%;
  }
  50% {
    bottom: 100%;
    transform: scale(0.7);
  }
  100% {
    bottom: 0%;
  }
} */

@keyframes cupUp {
  0% {
    bottom: 0%;
  }
  50% {
    bottom: 100%;
    transform: scale(0.7);
  }
  100% {
    bottom: 0%;
  }
}

@-webkit-keyframes cup1AroundUp {
  0% {
    transform: rotate(-180deg) translateX(0px) rotate(180deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(50vh) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(0deg) translateX(100vh) rotate(0deg) scale(1);
  }
}
@keyframes cup1AroundUp {
  0% {
    transform: rotate(-180deg) translateX(0px) rotate(180deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(50vh) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(0deg) translateX(100vh) rotate(0deg) scale(1);
  }
}
@-webkit-keyframes cup1AroundDown {
  0% {
    transform: rotate(180deg) translateX(0px) rotate(-180deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(25vh) rotate(-90deg) scale(1.3);
  }
  100% {
    transform: rotate(0deg) translateX(50vh) rotate(0deg) scale(1);
  }
}
@keyframes cup1AroundDown {
  0% {
    transform: rotate(180deg) translateX(0px) rotate(-180deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(25vh) rotate(-90deg) scale(1.3);
  }
  100% {
    transform: rotate(0deg) translateX(50vh) rotate(0deg) scale(1);
  }
}
@-webkit-keyframes cup2AroundUpRight {
  0% {
    transform: rotate(-180deg) translateX(0px) rotate(180deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(0deg) translateX(475%) rotate(0deg) scale(1);
  }
}
@keyframes cup2AroundUpRight {
  0% {
    transform: rotate(-180deg) translateX(0px) rotate(180deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(0deg) translateX(475%) rotate(0deg) scale(1);
  }
}
@-webkit-keyframes cup2AroundDownRight {
  0% {
    transform: rotate(180deg) translateX(0px) rotate(-180deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(1.3);
  }
  100% {
    transform: rotate(0deg) translateX(475%) rotate(0deg) scale(1);
  }
}
@keyframes cup2AroundDownRight {
  0% {
    transform: rotate(180deg) translateX(0px) rotate(-180deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(1.3);
  }
  100% {
    transform: rotate(0deg) translateX(475%) rotate(0deg) scale(1);
  }
}
@-webkit-keyframes cup2AroundUpLeft {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(-180deg) translateX(475%) rotate(180deg) scale(1);
  }
}
@keyframes cup2AroundUpLeft {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(-180deg) translateX(475%) rotate(180deg) scale(1);
  }
}
@-webkit-keyframes cup2AroundDownLeft {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(0.7);
  }
  100% {
    transform: rotate(180deg) translateX(475%) rotate(-180deg) scale(1);
  }
}
@keyframes cup2AroundDownLeft {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(0.7);
  }
  100% {
    transform: rotate(180deg) translateX(475%) rotate(-180deg) scale(1);
  }
}
@-webkit-keyframes cup3AroundUp {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(-180deg) translateX(475%) rotate(180deg) scale(1);
  }
}
@keyframes cup3AroundUp {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(-90deg) translateX(238%) rotate(90deg) scale(0.7);
  }
  100% {
    transform: rotate(-180deg) translateX(475%) rotate(180deg) scale(1);
  }
}
@-webkit-keyframes cup3AroundDown {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(0.7);
  }
  100% {
    transform: rotate(180deg) translateX(475%) rotate(-180deg) scale(1);
  }
}
@keyframes cup3AroundDown {
  0% {
    transform: rotate(0deg) translateX(0px) rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(90deg) translateX(238%) rotate(-90deg) scale(0.7);
  }
  100% {
    transform: rotate(180deg) translateX(475%) rotate(-180deg) scale(1);
  }
}/*# sourceMappingURL=main.css.map */
</style>