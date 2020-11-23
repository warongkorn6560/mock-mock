<template>
  <div>
    <div class="md:flex justify-between h-screen">
      <div class="w-2/12 sidebar"><ContentSwiper /></div>
      <div><Fabric /></div>
      <div class="w-2/12 sidebar"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.sidebar {
  background-color: #e3e4e3;
}
</style>