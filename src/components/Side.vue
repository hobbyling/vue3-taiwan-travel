<template>
  <div class="side">
    <img src="../assets/logo.svg" alt="Travel Logo" class="logo">
  </div>
</template>

<script>
export default {
  name: 'Side'
}
</script>

<style lang="scss" scoped>
.side {
  padding: 40px 24px;
  display: flex;
  flex-direction: column;

  // Logo
  .logo {
    width: 116.5px;
    height: 47px;
  }
}
</style>
