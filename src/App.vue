<template>
  <div id="app">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" crossorigin="anonymous" />
    <div id="page-container">
      <header>
        <span id="myName">
          <router-link to="/" exact> <span id="myName2"> Antoine Brault </span> </router-link>
          <hr />
        </span>
        <div id="allNavMobile">
          <div class="navIcon" v-if="mobileView">
            <transition name="burger">
              <i class="fas fa-bars" v-on:click="navBar = !navBar" v-if="!navBar"></i>
            </transition>
            <transition name="cross">
              <i class="fas fa-times" v-on:click="navBar = !navBar" v-if="navBar"></i>
            </transition>
          </div>
          <transition name="navigationMobile">
            <div v-if="navBar && mobileView" id="navMobile">
              <nav>
                <ul>
                  <li>
                    <router-link to="/publications"> Publications </router-link>
                    <hr />
                  </li>
                  <!-- <span v-if='linkActive'><hr></span> -->
                  <li>
                    <router-link to="/talks">Talks </router-link>
                    <hr />
                  </li>
                  <li>
                    <router-link to="/teaching">Teaching </router-link>
                    <hr />
                  </li>
                  <li>
                    <router-link to="/cv">CV </router-link>
                    <hr />
                  </li>
                </ul>
              </nav>
            </div>
          </transition>
        </div>
        <nav v-show="!mobileView">
          <ul>
            <li>
              <router-link to="/publications"> Publications </router-link>
              <hr />
            </li>
            <!-- <span v-if='linkActive'><hr></span> -->
            <li>
              <router-link to="/talks">Talks </router-link>
              <hr />
            </li>
            <li>
              <router-link to="/teaching">Teaching </router-link>
              <hr />
            </li>
            <li>
              <router-link to="/cv">CV </router-link>
              <hr />
            </li>
          </ul>
        </nav>
      </header>
      <div id="asideAndSection">
        <aside class="photo">
          <router-link to="/" exact><img src="./assets/moiCompresse.jpeg" alt="photoProfil" id="photoProfil"/></router-link>
          <p id="legendPhoto">
            Postdoc in applied mathematics at <a target="_blank" href="http://www.cmm.uchile.cl/">Center for Mathematical Modeling</a> in
            <a target="_blank" href="https://www.uchile.cl/english"> University of Chile</a>.<br /><br />
            <span class="tags"> <i class="far fa-envelope"></i> &nbsp; <a href="mailto:abrault@dim.uchile.cl">abrault@dim.uchile.cl</a> </span><br />
            <span class="tags"> <i class="fab fa-github"></i>&nbsp; <a target="_blank" href="https://github.com/AntoineBraultChile"> My github</a> </span><br /><br />
            <span class="tags"> I created a website to follow the Covid-19 pandemic in Chile: <a href="https://siguecovid.cl" target="_blank">siguecovid.cl</a> </span>
          </p>
        </aside>
        <section>
          <transition name="section">
            <router-view />
          </transition>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      mobileView: false,
      navBar: false,
    };
  },
  // methods: {
  //   handleView:function (){
  //     if (window.innerWidth <= 870){
  //       this.mobileView = true
  //     }
  //   }
  // },
  mounted() {
    window.addEventListener("resize", () => {
      this.mobileView = window.innerWidth <= 850;
    });
  },
  // created(){
  //   this.handleView();
  // }
};
</script>

<style>
hr {
  width: 100%;
  background-color: grey;
  height: 1px;
  border: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

body {
  width: auto;
  margin: 0;
  padding: 0px 10px 0px 10px;
  background-color: #edf3f3;
  /* overflow-y: hidden; /* Hide scrollbars */
  -ms-overflow-style: none; /* IE and Edge */
  /* background-color:#F9F2D8; */
}
/* Disable scrollbar Firefox*/
@-moz-document url-prefix() {
  html {
    scrollbar-width: none;
  }
}

body::-webkit-scrollbar {
  display: none;
}

#page-container {
  width: 1100px;
  /* min-width:870px; */
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  /* border-style: solid; */
  font-size: 20px;
  font-weight: lighter;
}

header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  font-size: 25px;
  padding: 30px 0px 20px 0px;
}

#myName {
  /* padding-left:0px;
  padding-right:10px; */
  text-align: center;
}

#myName2 {
  font-weight: bold;
  font-size: 40px;
}

nav {
  width: 68%;
}
nav ul {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

a {
  color: black;
  text-decoration: underline;
}

a:hover {
  text-decoration: underline;
}

header a {
  text-decoration: none;
  font-weight: normal;
  color: black;
}

header a:hover {
  color: black;
  text-decoration: none;
}

a + hr {
  display: block;
  height: 3px;
  margin: 0;
  margin-top: 4px;
  background: black;
  border: none;
  opacity: 1;
  transform: scale(0);
  transition: 100ms;
}

a:hover + hr,
a.router-link-exact-active + hr {
  display: block;
  height: 3px;
  margin: 0;
  margin-top: 4px;
  background: black;
  border: none;
  opacity: 1;
  transform: scale(1);
}

nav ul li {
  /* border: solid; */
  padding: 0px 0px 0px 0px;
  list-style: none;
}

#asideAndSection {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 0px 0px 0px 0px;
}

#photoProfil {
  width: 250px;
  border-radius: 100%;
  padding-left: 10px;
}

.photo {
  width: 30%;
  padding: 25px 0px 0px 0px;
}
.tags {
  display: inline;
}

#legendPhoto {
  font-size: 15px;
  text-align: justify;
}

section {
  padding: 0px 0px 0px 90px;
  text-align: left;
  width: 70%;
}

section ul {
  list-style: circle;
  padding-left: 20px;
}

h3 {
  line-height: 0.2em;
}

.bold {
  font-weight: bold;
}

.section-enter-active,
.section-leave-active {
  transition: opacity 0s, transform 0.2s;
}

.section-enter {
  position: absolute;
  opacity: 0;
  transform: translateY(+20%);
}

.section-leave-to {
  position: absolute;
  opacity: 0;
}

@media all and (max-width: 1100px) {
  #page-container {
    width: 100%;
  }
}

@media all and (max-width: 850px) {
  #page-container {
    margin: 0 auto;
    width: 100%;
    font-size: 20px;
  }

  header {
    flex-direction: row;
    padding: 0px 0px 0px 10px;
    font-size: 20px;
  }
  #myName2 {
    font-weight: bold;
    font-size: 20px;
  }
  /* nav ul {
      flex-direction:row;
    } */
  section {
    padding: 0px 0px 0px 0px;
    text-align: justify;
    width: 100%;
  }
  .photo {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 0px 0px 0px 0px;
  }
  #photoProfil {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    padding-right: 10px;
  }
  #asideAndSection {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0px 5px 0px 5px;
  }
  section {
    font-size: 15px;
  }

  .navIcon {
    padding: 5px 5px 5px 0px;
    text-align: right;
  }
  .navIcon i {
    font-size: 1.8rem;
  }
  #navMobile {
    position: absolute;
    right: 130px;
    top: 20px;
  }
  #navMobile nav ul {
    flex-direction: column;
    position: absolute;
    z-index: 100;
    background-color: #edf3f3;
    padding: 10px 10px 10px 10px;
    border: solid 1px;
    border-radius: 10%;
  }

  #navMobile a {
    text-decoration: none;
  }
  #navMobile nav ul {
    padding: 5px 5px 0px 5px;
  }

  #navMobile nav ul li {
    list-style: none;
    align-items: center;
    padding: 0px 0px 5px 0px;
    margin: 0px 0px 0px 0px;
  }

  .burger-enter-active {
    transition: opacity 0.2s;
    transition-delay: 0.2s;
  }

  .cross-enter-active,
  .cross-leave-active {
    transition: transform 0.2s, opacity 0.2s;
  }
  .burger-enter {
    position: absolute;
    opacity: 0;
  }
  .cross-enter {
    position: absolute;
    transform: rotate(90deg);
    opacity: 0;
  }

  .burger-leave,
  .cross-leave {
    opacity: 0;
  }

  .cross-leave-to {
    transform: rotate(90deg);
    opacity: 0;
  }

  a + hr {
    display: block;
    /* height: .25rem; */
    height: 2px;
    margin: 0px 0px 0px 0px;
    background: black;
    opacity: 1;
    transform: scale(0);
    transition: 100ms;
  }

  a:hover + hr,
  a.router-link-exact-active + hr {
    height: 2px;
    margin: 0px 0px 0px 0px;
    background: black;
  }

  .navigationMobile-enter-active,
  .navigationMobile-leave-active {
    transition: transform 0.1s ease-in-out;
  }

  .navigationMobile-enter-to {
    transform: scaleY(1);
  }
  .navigationMobile-enter,
  .navigationMobile-leave-to {
    transform: scaleY(0);
  }
}
</style>
