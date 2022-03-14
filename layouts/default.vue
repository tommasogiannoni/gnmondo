<template>
  <div>
    <div class="container" style="float=right; display: flex; align-items: end; justify-content: space-between;">
      <div>
        <img class="logo" src="~/assets/logognm.png" />
      </div>
      <div class="menu">
        <ul>
          <li>
            <NuxtLink to="/" class="text-decoration-none">Events</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/about" class="text-decoration-none">About Us</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
    <main>
      <!--img src="~/assets/logognm.png" /-->
      <Nuxt />
    </main>
  </div>
</template>

<style>
/* home route and active route will show in bold as it matches / and /about */

.logo {
  transition: 0s;
  margin-bottom: 0px; 
  margin-top: 30px; 
  width: 20%;
}
.logo:hover {
  transform: scale(1.2);
  -webkit-transition: transform 1s ease-in-out;
}
.menu{
  margin-bottom: 80px;
}
a.nuxt-link-active {
  font-weight: bold;
}
/* exact link will show the primary color for only the exact matching link */
a.nuxt-link-exact-active {
  color: #00c58e;
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

nav {
  padding: 0 1rem;
}

a,
a:visited {
  text-decoration: none;
  color: inherit;
}

a:hover {
  color: #00c58e;
}


</style>
