<template>
  <div class="sphere-container">
    <div class="sphere"></div>
  </div>
</template>

<style lang="scss" scoped>
.sphere-container {
  perspective: 1000px;
}

.sphere {
  width: 100px;
  height: 100px;
  background: linear-gradient(to right, #ff0000, #0000ff);
  border-radius: 50%;
  animation: rotate 5s infinite linear;
  transform-style: preserve-3d;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
