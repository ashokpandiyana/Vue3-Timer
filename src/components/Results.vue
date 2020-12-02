<template>
  <div class="block">Score : {{ value }} ms</div>
</template>

<script>
export default {
  name: "Results",
  props: ["value"],
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: rgb(2, 230, 154);
  color: rgb(255, 255, 255);
  text-align: center;
  margin: 10px auto;
  padding: 100px 0;
  cursor: pointer;
}
</style>
