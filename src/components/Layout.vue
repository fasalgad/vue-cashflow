<template>
  <div class="header">
    <slot name="header"></slot>
  </div>
  <div class="resume">
    <slot name="resume"></slot>
  </div>
  <div class="movements">
    <div class="head" @click="showMovements = !showMovements">
      <div class="grip"></div>
    </div>
    <transition name="slide">
      <div v-show="showMovements" class="body">
        <slot name="movements"></slot>
      </div> 
    </transition>
  </div>
</template>

<script setup>
import { ref } from "vue";
const showMovements = ref(false);
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
  background-color: #f5f5f5;
}
 
  .slide-enter-active,
  .slide-leave-active {
    transition: transform 0.3s;
  }

  .slide-enter-from,
  .slide-leave-to {
    transform: translateY(100%);
  }


.header,
.resume,
.movements {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 14px 0;
  box-sizing: border-box;
}

.header {
  position: fixed;
  width: 100vw;
}

.resume {
  min-height: 100vh;
}

.movements {
  z-index: 1;
  position: absolute;
  flex-direction: column;
  bottom: 0;
  width: 100vw;
  background-color: white;
  box-shadow: 0 -8px 16px #e5e5e5;
  border-radius: 24px;
}

.movements .head {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 24px;
  width: 100%;
  box-sizing: border-box;
}

.movements .body {
  height: 75vh;
  width: 100%;
}

.movements .head .grip {
  width: 120px;
  height: 8px;
  background-color: #e5e5e5;
  border-radius: 4px;
}
</style>
