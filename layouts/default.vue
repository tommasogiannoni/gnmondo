<template>
    <div>
      <div class="container" style="">
        <div style="text-align: center;">
          <img class="logo" src="~/assets/logognm.png" />
        </div>
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
      </div>
      <div class="line">
      </div>
      <main>
        <Nuxt />
      </main>
      <div class="footer">
        <div class="row">
          <span style="font-weight: lighter;"><span style="font-weight: bolder;">Copyright ©</span> GNM 2022 Tutti i diritti riservati</span>
        </div>
        <div class="row">
          <span>Powered by <b-link href="">Link</b-link></span>
        </div>
      </div>
    </div>
</template>

<script>
</script>

<style>
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
.menu{
  margin-bottom: 50px;
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
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto,
    Helvetica Neue, Arial, Noto Sans, sans-serif, Apple Color Emoji,
    Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
  margin: 0;
}

main {
  margin: 0 auto;
  padding: 0 1rem;
  margin-top: 100px;
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
