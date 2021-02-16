<template>
  <div id="app">
    <h2>Routing</h2>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link
        :to="{
          name: 'User',
          params: { id: 10 },
          query: { status: 'awesome' },
        }"
        >User With ID</router-link
      >
    </div>
    <hr />
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
