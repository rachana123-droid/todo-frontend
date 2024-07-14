<template>
  <div id="app">
    <div class="app-container">
      <nav class="nav-links">
        <router-link to="/" class="nav-link">Home</router-link> |
        <router-link to="/about" class="nav-link">About</router-link>
      </nav>
      <router-view/>
    </div>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #f0f0f0; /* Set a light background color */
  min-height: 100vh; /* Ensure app takes full viewport height */
  display: flex; /* Use flexbox for centering */
  justify-content: center; /* Center content horizontally */
  align-items: center; /* Center content vertically */
}

.app-container {
  width: 100%;
  max-width: 800px; /* Adjust maximum width as needed */
  margin: 20px; /* Add space around the container */
  padding: 20px; /* Add internal spacing within the container */
  border: 1px solid #ccc; /* Add a border */
  border-radius: 8px; /* Rounded corners */
  background-color: #fff; /* White background */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Subtle box shadow for depth */
}

.nav-links {
  padding: 10px; /* Add padding around navigation links */
}

.nav-link {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  margin: 0 10px; /* Add margin between navigation links */
}

.nav-link:hover {
  color: #42b983; /* Change link color on hover */
}
</style>
