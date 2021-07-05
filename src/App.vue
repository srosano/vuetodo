<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/layout/Header.vue";

export default {
  name: "app",
  components: {
    Header,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}
body {
  line-height: 1.4;
  font-family: Arial, Helvetica, sans-serif;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>
