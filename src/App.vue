<template>
  <div id="app">
    <MyHeader />
    <main id="main">
      <router-view />
    </main>
    <MyFooter />
  </div>
</template>

<style>
body,
ul,
li,
h1,
h2,
p {
  padding: 0;
  margin: 0;
}
body {
  font-family: "Segoe UI", serif;
  color: #334455;
  background: url(./assets/pattern.svg) repeat top;
}

a {
  color: #345;
  text-decoration: none;
}
ul {
  list-style: none;
}
* {
  box-sizing: border-box;
}

img {
  display: block;
  max-width: 100%;
}
.btn {
  display: block;
  padding: 10px 30px;
  background: #87f;
  border-radius: 4px;
  color: #ffffff;
  text-align: center;
  font-size: 1rem;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.2);
  transition: all 0.3s;
  font-family: "Segoe UI", serif;
  cursor: pointer;
}
.btn:hover {
  background: #6655dd;
  transform: scale(1.1);
}
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
#main {
  flex: 1;
}
</style>
<script>
import MyHeader from "@/components/MyHeader";
import MyFooter from "@/components/MyFooter";
export default {
  components: {
    MyHeader,
    MyFooter,
  },
};
</script>
