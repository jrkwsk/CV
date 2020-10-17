<template>
  <div id="app" @scroll="moveElements">
    <div class="wrapper-start" v-show="step===1">
      <div class="main-text d-flex justify-content-center align-items-end">
        <h1 class>ULA JURKOWSKA</h1>
      </div>
      <div class="secondary-text d-flex justify-content-center align-items-end">
        <h2 class="roles">
          <span>Developer</span>
          <span class="dot mb-1"></span>

          <span>Designer</span>
          <span class="dot mb-1"></span>

          <span>Project Manager</span>
        </h2>
      </div>
      <div class="d-flex justify-content-center my-5">
        <span class="show" @click="step++">I WANT TO SEE MORE</span>
      </div>
    </div>
    <!-- for scrolling effects -->
    <div class="middle" id="middle"></div>

    <transition name="showstep2">
      <div class="wrapper-next" v-show="step===2">
        <!-- <p class="document-title">Ula_Jurkowska_CV_late_2020</p> -->

        <div class="container section-1 d-flex flex-column align-items-stretch mt-5">
          <h4 class="main-skills h-100">
            <span class="important">VUE CLI</span>,
            <span class="important">Javascript ES6</span>, HTML, CSS, Bootstrap, JQuery,
            <span class="important">SASS</span>, Wordpress, WooCommerce,
            <span class="important">Rest API</span>, GIT, VS Code
          </h4>
          <h4 class="secondary-skills h-100">
            Photoshop, Ilustrator, inDesign,
            <span class="important">XD</span>
          </h4>
          <h4 class="secondary-skills h-100">
            English C1, French C1/B2, Spanish C1/B2
            <span class="important">&</span> Polish native
          </h4>
          <p
            class="about h-100"
          >I am a Psychologist, a Public Relations Manager, a Graphic Designer and a Web Developer. I speak Polish, English, French and Spanish. I try to make use of my various experiences in web development. I have participated in digital projects from different perspectives - as a user, an ordering entity, a designer and a coder. I believe my past roles give me a broad look on the work of a web developer being part of a team that delivers complex services to the client.</p>
          <p class="h-100 mt-5">
            Current focus on: Vue and Vanilla JS
            <strong class="ml-3">Goals:</strong> React, React Native, Angular
          </p>
          <div class="d-flex justify-content-center my-5 h-100">
            <div class="hor-line align-center"></div>
            <span class="scroll mx-2" id="scroll">scroll</span>
          </div>
        </div>
        <br />

        <div class="container-fluid IT-section text-left my-5">
          <div class="row my-5">
            <div class="col-2 title">
              <h1 class="it" id="it" :style="{paddingLeft: textPadding + 'rem'}">IT_Education</h1>
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
        <br />
        <div class="container my-5 text-center projects-sections">
          <h1>Projects - web</h1>
          <div class="row">
            <Project v-for="project in projects" :project="project"></Project>
          </div>
        </div>
        <div class="container my-5 text-center other">
          <h1>Other coding projects</h1>
          <div
            class="text-left d-flex justify-content-around github-sections"
            v-for="item in github"
            :key="item.name"
          >
            <a :href="item.link" target="_blank" @mouseover="moveDots($event)">
              <p class="project-name px-3 my-5">{{item.name}}</p>
            </a>
            <span class="dot my-5"></span>
            <p class="my-5">{{item.description}}</p>
            <p class="my-5">/</p>
            <p class="my-5">{{item.stack}}</p>
          </div>
        </div>
        <br />
        <div class="container experience-section text-left my-5">
          <h1>Professional Experience</h1>
          <div class="row my-5">
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

        <div class="container-fluid my-5 contact-section">
          <hr />
          <div class="row text-left">
            <div class="col-2 offset-1">
              <h1 class="contact">Contact</h1>
            </div>
            <div class="col-3 offset-1">
              <a href="u.jrkwsk@wp.pl">
                <img class="contact m-3" src="./assets/email-24px.svg" alt />
              </a>
              <a href="github.com/jrkwsk">
                <img class="contact m-3" src="./assets/g.png" alt />
              </a>
              <a href="linkedin.com/in/ula-jurkowska-27217830">
                <img class="contact m-3" src="./assets/l.png" alt />
              </a>
            </div>
            <div class="col-4 consent">
              <p
                class="font-italic"
              >Wyrażam zgodę na przetwarzanie moich danych osobowych przez firmy zarejestrowane w Polsce w celu prowadzenia rekrutacji na stanowisko Frontend Developer lub pokrewne</p>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import Project from "./components/Project.vue";

// import PortfolioNew from PortfolioNew.vue
// import PortfolioOld from PortfolioOld.vue
// import Musician from Musician.vue
// import Novel from Novel.vue

export default {
  name: "app",
  components: {
    Project
  },
  data() {
    return {
      step: 1,
      setOpacity: 0,
      imagePadding: 1,
      textPadding: 10,
      github: [
        {
          name: "Image search with NASA API",
          link: "https://github.com/jrkwsk/vue-app-nasa",
          description: "educational project with Hello Roman",
          stack: "VUE, JS, RESTAPI, ANXIOS "
        },
        {
          name: "Photo slider",
          link: "https://github.com/jrkwsk/vue-slider-app",
          description: "educational project with P.Palarz",
          stack: "VUE"
        },
        {
          name: "Stocks app",
          link: "https://github.com/jrkwsk/angularapp1",
          description: "first project to get familiar with Angular",
          stack: "ANGULAR"
        },
        {
          name: "Simple form",
          link: "https://github.com/jrkwsk/vue-form",
          description: "educational project on inputs in Vue",
          stack: "VUE"
        },
        {
          name: "The Witcher game ;)",
          link: "https://github.com/jrkwsk/vuegame",
          description: "simple game in VUE",
          stack: "VUE"
        },
        {
          name: "Photo search",
          link: "https://github.com/jrkwsk/rest-api-unsplash",
          description: "photosearch with Unsplash API",
          stack: "REST API"
        },
        {
          name: "Some scroll animations",
          link: "https://github.com/jrkwsk/scrolleffects",
          description: "excesise on animations with JS",
          stack: "HTML, CSS, JS"
        },
        {
          name: "Recipes app",
          link: "https://github.com/jrkwsk/recipesapp",
          description: "first project to get familiar with React",
          stack: "REACT"
        },
        {
          name: "3D models with JS",
          link: "https://github.com/jrkwsk/openjscad",
          description: "project to get familiar with OpenJSCAD",
          stack: "OpenJSCAD"
        },
        {
          name: "Flying dots",
          link: "https://github.com/jrkwsk/easejs_ex/",
          description: "project to get familiar with CREATEJS",
          stack: "CREATEJS"
        },
        {
          name: "Ticking clock",
          link: "https://github.com/jrkwsk/clock",
          description: "traditional clock coded in JS",
          stack: "JS"
        },
        {
          name: "Simple photo- gallery",
          link: "https://github.com/jrkwsk/gallery",
          description: "gallery - SEO purposes",
          stack: "BOOTSTRAP"
        },
        {
          name: "E-commerce banner",
          link: "https://github.com/jrkwsk/task_jquery/",
          description: "recruitment tasked for JQUERY usage",
          stack: "JQUERY"
        },
        {
          name: "Openstreetmap app",
          link: "https://github.com/jrkwsk/map",
          description: "getting familiar with a popular map library",
          stack: "LEAFLET"
        }
      ],
      projects: [
        {
          name: "Quiz - app",
          stack: "VUE CLI, Vanilla JS, SASS, Bootstrap, Firebase",
          status: "ongoing",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: false,
          github: "https://github.com/jrkwsk/billenn-quiz",
          task: "code",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Portfolio 2020",
          stack: "VUE CLI, Vanilla JS, SASS, Bootstrap",
          status: "ongoing",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: false,
          github: "github",
          task: "code & design",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Maptu (2020)",
          stack: "XD, Photoshop",
          status: "to be published",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "https://maptu.pl/",
          github: false,
          task: "design only",
          button1: "website",
          button2: "project"
        },
        {
          name: "Maptu (2019)",
          stack: "Vanilla JS, Bootstrap, Photoshop",
          status: "finished",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "http://jrkwsk.pl/maptu2019",
          github: "https://github.com/jrkwsk/commercialproject1",
          task: "code & design",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Maptu Shop (2019)",
          stack: "Woocommerce",
          status: "finished",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "demo",
          github: "github",
          task: "code & design",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Maptu (2015)",
          stack: "Photoshop",
          status: "finished",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "demo",
          github: "github",
          task: "design only",
          button1: "demo",
          button2: "project"
        },
        {
          name: "Musician (2019)",
          stack: "VUE CLI, Vanilla JS, SASS, Bootstrap",
          status: "ongoing",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "demo",
          github: "github",
          task: "code & design",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Portfolio (2018)",
          stack: "Vanilla JS, Bootstrap",
          status: "finished",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "demo",
          github: "github",
          task: "code & design",
          button1: "demo",
          button2: "code"
        },
        {
          name: "Novel (2018)",
          stack: "Vanilla JS, Bootstrap",
          status: "to be updated",
          img: "http://jrkwsk.pl/img/c.jpg",
          demo: "http://www.bluetongue.me/",
          github: "github",
          task: "code & design",
          button1: "demo",
          button2: "code"
        }
      ],
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
      //animate elements when they reach the middle of window
      const middle = document.getElementById("middle").getBoundingClientRect()
        .top;
      let elementsAnimated = Array.from(
        document.getElementsByClassName("start-end")
      );
      elementsAnimated.forEach(elem =>
        elem.getBoundingClientRect().top < middle
          ? elem.classList.add("animated")
          : console.log("error")
      );
      //change opacity while scrolling
      const imagePosition = document
        .querySelector("img")
        .getBoundingClientRect().bottom;
      this.setOpacity = (imagePosition + 100) / 1000;

      //slower img moving depending on scrol x padding-top
      this.imagePadding = imagePosition / 50;

      this.textPadding = this.textPadding - 0.1;

      let textIt = document.getElementById("it");

      if (textIt.getBoundingClientRect().bottom < -200) {
        textIt.style.position = "relative";
        textIt.removeAttribute("id");
        textIt.style.transform = "rotate(90deg)";
        textIt.style.opacity = 0.2;
      }
    },
    moveDots($event) {
      let dot1 = $event.target.nextElementSibling;
      dot1.classList.toggle("pulse");
      console.log(dot1);
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
$navy: #2a435b;
$blue: #85a8be;
$yellow: #f1bd5a;
$orange: #f2ab59;

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
  background-color: $color-secondary-4;
}

//first slaid

div.wrapper-start {
  background-color: $color-secondary-4;
  h2.roles {
    background-color: $color-secondary-4;

    span {
      color: $blue;
      font-size: 2rem;
    }
  }
  div.main-text {
    height: 40vh;
  }
  h1 {
    font-weight: normal;
    font-size: 5rem;
  }
  h2 {
    color: $yellow;
    font-size: 2rem;
  }
  span.show {
    font-family: $font-secondary;
    font-weight: 300;
    font-style: normal;
    font-size: 1rem;
    transition: all 2s;
    background-color: transparent;
    border-color: transparent;
    display: inline-block;
    cursor: pointer;
    font-weight: 100;
  }

  span.show:hover {
    border-bottom: 2px solid $color-primary;
  }
}

//second slide

div.section-1 {
  width: 100vw;
  height: 100vh;
}

h4.main-skills {
  margin-top: 15vh;
  color: $color-primary;
  font-size: 2rem;
}
h4.secondary-skills {
  color: $color-secondary;
}
span {
  font-size: 2.5rem;
}

span.important {
  font-size: 3rem;
  color: $yellow;
}

div.hor-line {
  width: 1px;
  height: 7vh;
  border-left: 1px solid black;
}

span.scroll {
  text-transform: uppercase;
  font-size: 0.8rem;
  // color: $blue;
  font-weight: 500;
  font-family: $font-secondary;
  // animation: pulse 1s infinite;
}

h2.roles {
  font-family: $font-secondary;
  text-transform: uppercase;
  font-weight: 100;
  font-kerning: normal;
}

div.middle {
  width: 1px;
  height: 1px;
  position: fixed;
  background: transparent;
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
  line-height: 3;
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

#it {
  color: $blue;
  transform: rotate(90deg);
  font-weight: 700;
  font-size: 3rem;
  transition: all 1s;
}

div.github-sections {
  font-family: $font-secondary;
}

span.dot {
  height: 10px;
  width: 10px;
  background-color: $orange;
  border-radius: 50%;
  display: inline-block;
}
p.project-name {
  background-color: $color-primary;
  color: $color-secondary-4;
}

div.arrow-right {
  width: 0;
  height: 0;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  border-left: 10px solid $color-secondary-2;
}

h1.it {
  transition: opacity 2s;
}
p.document-title {
  position: fixed;
  top: 0;
}
span.pulse {
  animation: pulse-red 5s infinite;
  transition: all 1s;
}

h1.contact {
  color: $color-secondary-2;
}

div.consent {
  color: $color-secondary-3;
}

@keyframes pulse-red {
  0% {
    transform: scale(2);
    box-shadow: 0 0 0 0 rgba(255, 82, 82, 0.7);
  }

  10% {
    transform: scale(1);
    box-shadow: 0 0 0 10px rgba(255, 82, 82, 0);
  }

  100% {
    transform: scale(2);
    box-shadow: 0 0 0 0 rgba(255, 82, 82, 0);
  }
}
//animated slide
.showstep2-enter-active {
  animation: shownew 2s;
}

@keyframes shownew {
  0% {
    transform: translateY(-100px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes pulse {
  0% {
    opacity: 1;
  }

  10% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}
</style>