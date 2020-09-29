<template>
  <div class="wrapper col-6">
    <div class="container my-5">
      <img class="w-100 h-100 project-img" :src="project.img" />
      <div class="overlay">
        <p class="name">see more:</p>
        <a :href="project.demo" target="_blank">
          <button class="more">{{project.button1}}</button>
        </a>
        <a :href="project.github" target="_blank">
          <button class="more">{{project.button2}}</button>
        </a>
      </div>
      <span class="title">{{project.name}} /</span>
      <span class="comment">{{project.status}}</span>
      <p class="stack">{{project.stack}}</p>
      <p class="task">{{project.task}}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["project"]
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

p.name {
  color: $color-secondary-4;
}

div.container {
  position: relative;
  margin: 0 auto;
}

img {
  display: block;
}
div.overlay {
  font-size: 3rem;
  position: absolute;
  top: 20%;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: all 0.5s;
}
div.overlay:hover {
  opacity: 1;
}
button.more {
  font-family: $font-secondary;
  color: $color-secondary-4;
  font-weight: 300;
  font-style: normal;
  font-size: 0.8rem;
  transition: all 1s;
  background-color: transparent;
  border-radius: 6px;
  border: 1px solid $color-secondary-4;
  display: inline-block;
  cursor: pointer;
  font-size: 15px;
  font-weight: bold;
  padding: 1rem 2rem;
  text-decoration: none;
}

button.more:hover {
  background-color: $color-secondary-4;
  color: $color-secondary-3;
}
button.more:active {
  position: relative;
  top: 1px;
}

p.stack {
  font-family: $font-secondary;
  font-weight: 100;
}

p.task {
  font-size: 0.7rem;
}
span.comment {
  font-size: 1rem;
}
</style> 