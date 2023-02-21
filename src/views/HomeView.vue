<template>
  <div class="navBar">
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li @click="show1f" :class="{ active: show1 }" class="button">
        <router-link to="/about"> About </router-link>
      </li>
      <li @click="show2f" :class="{ active: show2 }" class="button">
        <router-link to="/teste">Teste</router-link>
      </li>
      <li @click="show3f" :class="{ active: show3 }" class="button">
        <router-link to="/">Home</router-link>
      </li>
    </ul>
  </div>
  <div class="upload">
    <Btn />
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Btn from "@/components/BtnUpload.vue"
const show1 = ref(false);
const show2 = ref(false);
const show3 = ref(false);

const resetf = () => {
  show1.value = false;
  show2.value = false;
  show3.value = false;
};

const show1f = () => {
  resetf();
  show1.value = true;
};
const show2f = () => {
  resetf();
  show2.value = true;
};
const show3f = () => {
  resetf();
  show3.value = true;
};
</script>

<style scoped>
.active a {
  background-color: #e7e7e7;
  color: black;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #002c27;
  display: flex;
  justify-content: center;
}
.navBar {
  margin-right: auto;
  margin-left: auto;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #e7e7e7;
  color: #002c27;
}

.subcontainer {
  margin-right: auto;
  margin-left: auto;
}
.logo {
  margin-left: 90px;
  padding: 0;
}
</style>
