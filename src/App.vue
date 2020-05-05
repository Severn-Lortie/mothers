<template>
  <div id="app" ref="app">
    <camera>
    </camera>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    camera: () => import('./components/Camera'),
  },
}
</script>

<style>
body {
  margin: 0px;
  background-image: url("https://images.unsplash.com/photo-1585207691254-68823f64e6aa?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1502&q=80");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
</style>
