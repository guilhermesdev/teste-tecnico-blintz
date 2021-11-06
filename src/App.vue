<template>
  <div class="container">
    <TheHeader class="mb-4" />
    <RealStateList />
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader';
import RealStateList from '@/components/RealStateList';

export default {
  name: 'App',
  components: {
    TheHeader,
    RealStateList
  }
}
</script>

<style lang="scss">
.container {
  width: 100%;
  padding: .3rem 1rem;
}
</style>
