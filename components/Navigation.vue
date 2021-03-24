<template>
  <div class="nav-container">
    <span ref="burger" class="nav-menu" @click="openNav()">&#9776;</span>
    <div ref="nav" class="nav-bar">
      <a class="closebtn" @click="closeNav()">&times;</a>
      <nuxt-link to="/">
        #Home
      </nuxt-link>
      <nuxt-link to="/add">
        #AddPerson
      </nuxt-link>
      <nuxt-link to="/overview">
        #Übersicht
      </nuxt-link>
    </div>
  </div>
</template>

<script>

export default {
  created () {

  },
  mounted () {

  },

  methods: {
    openNav () {
      if (window.innerWidth < 600) {
        this.$refs.nav.style.width = '100vw'
      } else {
        this.$refs.nav.style.width = '250px'
      }
      this.$refs.burger.style.visibility = 'hidden'
    },
    closeNav () {
      this.$refs.nav.style.width = '0'
      this.$refs.burger.style.visibility = 'visible'
    }
  }
}
</script>

<style scoped>
.nav-container {
  width: 0;
  height: 0;
}

.nav-menu {
  position: fixed;
  top: 0;
  left: 10px;
  cursor: pointer;
  font-size: 40px;
  animation: 1s appear;
}

.nav-bar {
  height: 100vh;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 60px;
}

.nav-bar a {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: 25px;
  color: white;
  display: block;
  transition: 0.3s;
}

.nav-bar a:hover {
  color: var(--secondary-color);
}

.nav-bar .closebtn {
  cursor: pointer;
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

@media screen and (max-width: 600px) {
  .nav-bar {
    text-align: center;
  }
}
</style>
