<script setup></script>

<template>
  <h1 class="title">
    <slot></slot>
  </h1>
</template>

<style scoped lang="scss">
.title {
  margin-bottom: 90px;
  padding-top: 70px;
  text-align: center;
  font-weight: 700;
  font-size: 36px;
  line-height: 120%;
  color: #000000;

  @media (max-width: 600px) {
    margin-bottom: 20px;
    font-weight: 500;
    font-size: 28px;
    line-height: 120%;
  }

  @media (max-width: 375px) {
    margin-bottom: 20px;
    font-weight: 500;
    font-size: 23px;
    line-height: 120%;
  }
}
</style>
