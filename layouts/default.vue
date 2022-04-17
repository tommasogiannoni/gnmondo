<template>
    <div class="body">

      <div class="header">
        <div class="container">
          <div style="text-align: center;">
            <img class="logo" src="~/assets/logognm.png" />
          </div>
        </div>
      </div>

      <div class="locked-header" id="myHeader">
        <div class="row menu">
              <ul>
                <li class="list-item">
                  <NuxtLink to="/" class="text-decoration-none">Eventi</NuxtLink>
                </li>
                <!--li class="list-item">
                  <NuxtLink to="/backoffice" class="text-decoration-none">Back-office</NuxtLink>
                </li-->
                <li class="list-item">
                  <NuxtLink to="/about" class="text-decoration-none">Chi Siamo</NuxtLink>
                </li>
              </ul>
        </div>
        <div class="line">
        </div>
      </div>

      <div class="main">
        <main>
          <Nuxt />
        </main>
      </div>

      <div class="footer">
        <div class="row">
          <span style="font-weight: lighter;">Copyright © <span style="font-weight: bolder;">GNM 2022</span> Tutti i diritti riservati</span>
        </div>
        <div class="row">
          <span>Powered by <b-link href="">***</b-link></span>
        </div>
      </div>

    </div>
</template>

<script>
export default {

  mounted() {
    window.addEventListener("scroll", this.onScroll)
    this.$refs.myHeader
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll)
  },
  methods: {
    onScroll(e) {
      //this.windowTop = window.top.scrollY /* or: e.target.documentElement.scrollTop */
      var header = document.getElementById("myHeader");
      var sticky = header.offsetTop;
      var topMargin = 190;
      
      if (window.pageYOffset > sticky) {
        header.classList.add("sticky");
      } 
      if ( window.pageYOffset < topMargin) {
        header.classList.remove("sticky");
      }
      
      
    }
  }
}
</script>

<style>
.locked-header {
  background: #EEEEEE;
  .menu{
    margin-bottom: 50px;
  }
}
.header {
  /*position: fixed; /*remove to disable locked header*/
  background: #EEEEEE;
}
.sticky {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 999;
}

.sticky + .main {
  padding-top: 50px;
}

/* home route and active route will show in bold as it matches / and /about */
.line{
  width: 100%;
  text-align: left;
  border-top: 3px solid #D8D2CB;
}
.logo {
  transition: 0s;
  margin-bottom: 0px; 
  margin-top: 30px; 
  width: 10rem;
  
}
.logo:hover {
  transform: scale(1.2);
  -webkit-transition: transform 1s ease-in-out;
}

.list-item{
  border-bottom-style: solid;
  border-bottom-color: #1C658C;
}

a.nuxt-link-active {
  font-weight: bold;
}
/* exact link will show the primary color for only the exact matching link */
a.nuxt-link-exact-active {
  color: #1C658C;
}

body {
  overflow-x: hidden;
}

.main {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto,
    Helvetica Neue, Arial, Noto Sans, sans-serif, Apple Color Emoji,
    Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;

  margin: 0 auto;
  padding: 0 1rem;
  margin-top: 50px;
  max-width: 1280px;
  text-align: center;
}
img {
  margin-bottom: 1rem;
}

ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
li {
  margin: 0 0.5rem;
  padding: 0.25rem;
  font-size: 1.2rem;
}



a,
a:visited {
  text-decoration: none;
  color: inherit;
}

a:hover {
  color: #D8D2CB;
}
.footer {
  width: 100%;
  background-color: #D8D2CB;
  height: 150px;
  justify-content: center;
  align-items: center;
  display: flex;
  flex-flow: column;
  font-size: 12px;
}


</style>
