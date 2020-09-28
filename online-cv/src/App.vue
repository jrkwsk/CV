<template>
  <div id="app" @scroll="moveElements">
    <div class="wrapper-start" v-show="step===1">
      <div class="main-text d-flex justify-content-center align-items-end">
        <h1 class>ULA JURKOWSKA</h1>
      </div>
      <div class="secondary-text d-flex justify-content-center align-items-end">
        <h2 class="roles">
          <span>/</span>Developer
          <span>/</span>Designer
          <span>/</span>Project_Manager
          <span>/</span>
        </h2>
      </div>
      <div class="d-flex justify-content-center align-items-end m-5">
        <button type="button" class="show" @click="step++">SHOW</button>
      </div>
    </div>
    <div class="middle" id="middle"></div>
    <div class="wrapper-next" v-show="step===2">
      <p>Ula_Jurkowska_CV_late_2020</p>
      <div class="container">
        <h4 class="main-skills">
          <span class="important">VUE CLI</span>,
          <span class="important">Javascript ES6</span>, HTML, CSS, Bootstrap, JQuery,
          <span class="important">SASS</span>, Wordpress, WooCommerce,
          <span class="important">Rest API</span>, GIT, VS Code
        </h4>
        <h4 class="secondary-skills mt-5">Photoshop, Ilustrator, inDesign, XD</h4>
        <h4 class="secondary-skills mt-5">English C1, French C1/B2, Spanish C1/B2 & Polish native</h4>
        <p
          class="mt-5 about"
        >I am a Psychologist, Public Relations Manager, Graphic Designer and Web Developer. I speak Polish, English, French and Spanish. I try to make use of my various experiences in web development. I have participated in digital projects from different perspectives - as a user, ordering entity, designer and coder. I believe my past roles give me a broad look on the work of web developer being part of a team that delivers complex services to the client.</p>
        <p class="mt-5">Current focus on: Vue and Vanilla JS</p>
        <p class="mt-5">Goals: React, React Native, Angular</p>
        <div class="d-flex justify-content-center my-5">
          <div class="hor-line align-center"></div>
          <span class="scroll mx-2">scroll</span>
        </div>
      </div>
      <br />
      <div class="container-fluid IT-section text-left my-5">
        <div class="row">
          <div class="col-2">
            <p class id="id">IT_Education</p>
          </div>
          <div class="col-6">
            <div class="basic-info" v-for="value in it" :key="it.position">
              <span class="start-end">{{value.year}}</span>
              <br />
              <span class>{{value.position}} /</span>
              <br />
              <span class="important">{{value.company}} /</span>
              <p class="about">{{value.description}}</p>
            </div>
          </div>
          <div class="col-4 img-wrapper" :style="{paddingTop: imagePadding + 'rem'}">
            <img class="portrait" src="./assets/portrait.jpg" :style="{opacity: setOpacity}" />
          </div>
        </div>
      </div>
      <hr />
      <div class="container experience-section text-left my-5">
        <div class="col-9 offset-3">
          <div class="basic-info" v-for="value in cv" :key="cv.position">
            <span class="start-end">{{value.start}} - {{value.end}}</span>
            <br />
            <span class>{{value.position}} /</span>
            <br />
            <span class="important">{{value.company}} /</span>
            <span class="minor">{{value.city}}, {{value.country}}</span>
            <p class="about">{{value.description}}</p>
            <p class="about">{{value.techStack}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      step: 1,
      setOpacity: 0,
      imagePadding: 1,
      it: [
        {
          position:
            "Vue - The Complete Guide (w/ Router, Vuex, Composition API)",
          company: "Maximilian Schwarzmüller",
          place: "Udemy.com",
          year: "2020",
          description: "Online"
        },
        {
          position: "The Complete JavaScript Course 2020: Build Real Projects!",
          company: "Jonas Schmedtmann",
          place: "Udemy.com",
          year: "2020",
          description: "Online"
        },
        {
          position: "Front End Developer",
          company: "Akademia 108",
          place: "Warsaw",
          year: "2018",
          description: "FrontEnd basics - Bootcamp"
        }
      ],
      cv: [
        {
          position: "Senior Analyst",
          company: "HCL",
          city: "Kraków",
          country: "Poland",
          start: "2018/08",
          end: "present",
          duration: "null",
          description:
            "Project for Google. Analyzing special cases for a new project on French speaking markets.",
          techStack: "dedicated Google tools, Agile, French C1"
        },
        {
          position: "Project Manager / Web Developer / Graphic Designer",
          company: "Maptu.pl",
          city: "Warsaw",
          country: "Poland",
          start: "2015/08",
          end: "2020/02",
          duration: "null",
          description:
            "Managing project Maptu.pl from developing the concept to selling well-working business",
          techStack:
            "HTML, CSS, BOOTSTRAP, JAVASCRIPT, JQUERY, WORDPRESS, WOOCOMMERCE, QGIS, PHOTOSHOP, ILLUSTRATOR, InDesign, XD"
        },
        {
          position: "Project Manager",
          company: "Compass PR",
          city: "Warsaw",
          country: "Poland",
          start: "2015/08",
          end: "2014/06",
          duration: "null",
          description:
            "Project management, PR services to the agency’s clients, mainly pharmaceutical companies. Clients: Roche, Pfizer, FoodCare",
          techStack: " "
        },
        {
          position: "Account Executive",
          company: "Lighthouse",
          city: "Warsaw",
          country: "Poland",
          start: "2011/05",
          end: "2014/08",
          duration: "null",
          description:
            "On-going PR service to the agency’s clients from various sectors. Close cooperation with the department Manager.  Dr. Oetker, Robert Bosch, Maastricht University, Orlen Gaz, Teva, PGE, Orange, BRE Bank",
          techStack: " "
        },
        {
          position: "PR & Administration Specialist",
          company: "SymKom",
          city: "Warsaw",
          country: "Poland",
          start: "2010/11",
          end: "2010/10",
          duration: "null",
          description:
            "Administrative work and PR activities for software seller",
          techStack: " "
        },
        {
          position: "Marketing Assistant",
          company: "Gide",
          city: "Warsaw",
          country: "Poland",
          start: "2010/02",
          end: "2010/10",
          duration: "null",
          description: "Assisting the Director in everyday work",
          techStack: "English C1, French C1, databases"
        },
        {
          position: "Volunteer",
          company: "Young Cinema Foundation",
          city: "Warsaw",
          country: "Poland",
          start: "2006/10",
          end: "2010/02",
          duration: "null",
          description:
            "Assisting the President in everyday work, organization of Euroshorts (short film festival)",
          techStack: " "
        }
      ]
    };
  },
  methods: {
    moveElements(event) {
      const middle = document.getElementById("middle").getBoundingClientRect()
        .top;
      let elementsAnimated = Array.from(
        document.getElementsByClassName("start-end")
      );
      elementsAnimated.forEach(
        elem =>
          elem.getBoundingClientRect().top < middle
            ? elem.classList.add("animated")
            : console.log("error")
        // console.log(elem.getBoundingClientRect().top)
        // elem.classList.add("red")
      );
      // if ((elem.getBoundingClientRect().top = window.innerHeight() / 2)) {
      //   elem.classList.add("red");
      // }

      // console.log(event.target.scrollTop);

      // let scrollTarget = event.target;
      // console.log(scrollTarget.scrollTop);
      // console.log(scrollTarget.scrollHeight);
      // console.log(scrollTarget.clientHeight);
      const imagePosition = document
        .querySelector("img")
        .getBoundingClientRect().bottom;
      this.setOpacity = (imagePosition + 100) / 1000;

      //slower img moving depending on scrol x padding-top
      this.imagePadding = imagePosition / 50;
    }
  }
};
</script>

<style lang="scss">
$font-primary: curve, serif;
$font-secondary: soleil, sans-serif;
$color-secondary-4: #f2f2f2;
$color-secondary-3: #a6a6a6;
$color-secondary-2: #737373;
$color-secondary: #404040;
$color-primary: #0d0d0d;

#app {
  font-family: curve, serif;
  font-style: normal;
  font-weight: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $color-primary;
  width: 100vw;
  height: 100vh;
  transition: all 1s;
  overflow-x: hidden;
}

div.main-text {
  height: 40vh;
}
h1 {
  font-weight: normal;
  font-size: 4rem;
}
#id {
  transform: rotate(90deg);
  font-weight: 700;
  font-size: 5rem;
  position: absolute;
  left: 0;
  // mix-blend-mode: screen;
  // margin: -5rem -0 0 0;
  // color: $color-secondary-2;
  color: pink;
  // opacity: 0.1;
}
h2 {
  color: black;
  mix-blend-mode: lighten;
  background-color: white;
  background-position: center;
  font-size: 1.3rem;
  width: 100vw;
  transform: translateY(2%);
  // box-sizing: border-box;
  margin: -5px;
  padding: 5px;
}

button.show {
  font-family: $font-secondary;
  font-weight: 300;
  font-style: normal;
  font-size: 0.8rem;
  transition: all 1s;
  background-color: transparent;
  border-radius: 6px;
  border: 1px solid $color-secondary-3;
  display: inline-block;
  cursor: pointer;
  color: $color-secondary-2;
  font-size: 15px;
  font-weight: bold;
  padding: 1rem 2rem;
  text-decoration: none;
}

button.show:hover {
  background-color: $color-secondary-3;
  color: $color-secondary-4;
}
button.show:active {
  position: relative;
  top: 1px;
}

div.secondary-text {
  background-image: url(assets/bg_0004.jpg);
  background-size: 40% 120%;
  background-repeat: no-repeat;
  background-position: center;
}

span {
  font-size: 2.5rem;
}

h4.main-skills {
  margin-top: 25vh;
  color: $color-primary;
  font-size: 2rem;
}
h4.secondary-skills {
  color: $color-secondary;
}

span.important {
  font-size: 3rem;
  color: $color-secondary-3;
}

div.hor-line {
  width: 1px;
  height: 7vh;
  border-left: 1px solid black;
}

span.scroll {
  text-transform: uppercase;
  font-size: 0.8rem;
  color: $color-secondary-3;
  font-weight: 100;
  font-family: $font-secondary;
}

h2.roles {
  font-family: $font-secondary;
  text-transform: uppercase;
  font-weight: 100;
  font-kerning: normal;
}

div.middle {
  width: 10px;
  height: 10px;
  position: fixed;
  background: blue;
  margin: 0 auto;
  top: 50%;
  left: 50%;
}

span.start-end {
  position: absolute;
  font-size: 0.9rem;
  font-family: $font-secondary;
  text-transform: uppercase;
  color: $color-secondary-3;
  font-weight: 100;
}
span.animated {
  transition: all 0.5s;
  transform: translate(-2vw, -0.5vh);
  position: absolute;
}

span.minor {
  font-size: 2.5rem;
}

p.about {
  color: $color-primary;
  font-family: $font-secondary;
  font-weight: 100;
  margin-top: 1rem;
}

div.basic-info {
  margin-bottom: 6vh;
}

img.portrait {
  width: 100%;

  transition: all 1s;
  opacity: 0.1;
  position: absolute;
}

img.wrapper {
  padding: 100px;
}
</style>