<template>
  <div class="Person">
    <img :src="$attrs.value">//хранилище атрибоутов src
  </div>
</template>

<style scoped>
  .Person {
    display: flex;
    justify-content: center;
  }
</style>