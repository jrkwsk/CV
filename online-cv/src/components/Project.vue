<template>
  <div class="wrapper col-6">
    <div class="container my-5">
      <div class="buttons-wrapper">
        <a :href="project.demo" target="_blank" v-show="project.demo">
          <p class="more px-3 my-5">{{project.button1}}</p>
        </a>
        <a :href="project.github" target="_blank" v-show="project.github">
          <p class="more px-3 my-5">{{project.button2}}</p>
        </a>
      </div>

      <div class="description">
        <span class="title">{{project.name}} /</span>
        <span class="comment">{{project.status}}</span>
        <p class="stack">{{project.stack}}</p>
        <p class="task">{{project.task}}</p>
      </div>
    </div>
  </div>
  <!-- <div class="wrapper col-6">
    <div class="container my-5">
      <img class="w-100 h-100 project-img" :src="project.img" />
      <div class="overlay">
        <p class="name">see more:</p>
        <a :href="project.demo" target="_blank" v-show="project.demo">
          <button class="more">{{project.button1}}</button>
        </a>
        <a :href="project.github" target="_blank" v-show="project.github">
          <button class="more">{{project.button2}}</button>
        </a>
      </div>
      <span class="title">{{project.name}} /</span>
      <span class="comment">{{project.status}}</span>
      <p class="stack">{{project.stack}}</p>
      <p class="task">{{project.task}}</p>
    </div>
  </div>-->
</template>
<script>
export default {
  props: ["project"],
  methods: {
    buttonAnimation() {
      const buttons = Array.from(document.getElementsByClassName("more"));
      console.log(buttons + "btnn anim");
      buttons.forEach(elem => elem.classList.addClass("animated"));
    }
  }
};
</script>
<style lang="scss" scoped>
// to do: globalize this variables:
$font-primary: curve, serif;
$font-secondary: soleil, sans-serif;
$color-secondary-4: #f2f2f2;
$color-secondary-3: #a6a6a6;
$color-secondary-2: #737373;
$color-secondary: #404040;
$color-primary: #0d0d0d;
$navy: #2a435b;
$blue: #85a8be;
$yellow: #f1bd5a;
$orange: #f2ab59;

p.name {
  color: $color-secondary-4;
}

div.container {
  position: relative;
  margin: 0 auto;
}

// img {
//   display: block;
// }

div.overlay {
  font-size: 3rem;
  position: absolute;
  top: 25%;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: all 0.5s;
}
div.overlay:hover {
  opacity: 1;
}

p.more {
  font-family: $font-secondary;
  color: $color-primary;
  font-weight: 300;
  font-style: normal;
  font-size: 0.8rem;
  transition: all 0.7s;
  background-color: transparent;
  border: 1px solid $color-primary;
  border-right: 1px solid transparent;

  display: inline-block;
  cursor: pointer;
  font-size: 15px;
  font-weight: bold;
  text-decoration: none;
  // border-left: 40px solid transparent;
}

p.more:hover {
  color: $color-primary;
  background-color: transparent;
  // border: 1px solid transparent;
  border-right: 15px solid $yellow;
}
p.more:active {
  position: relative;
  top: 1px;
}

.animated {
  color: $color-secondary-4;
  background-color: $color-primary;
}

p.stack,
p.task {
  font-family: $font-secondary;
  font-weight: 100;
}

p.task {
  font-size: 0.9rem;
}
span.comment {
  font-size: 1rem;
}
</style> 