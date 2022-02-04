<template>
  <div class="main-container">
    <slot />
  </div>
</template>

<script>
  export default {
    name: 'MainContainer',
  };
</script>

<style lang="scss" scoped>
  .main-container {
    max-width: $window-width-desktop;
    width: 100%;
    margin: 0 auto;
  }
</style>
