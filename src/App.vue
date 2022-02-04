<template>
  <TheHeader />

  <router-view />
</template>

<script>
  import TheHeader from '@/components/layout/TheHeader';

  export default {
    components: {
      TheHeader,
    },
  };
</script>

<style lang="scss"></style>
