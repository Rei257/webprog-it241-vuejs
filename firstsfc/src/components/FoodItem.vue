<template>
  <div class="santol">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Orange and Apple',
      message: 'I like Orange and Apple'
    }
  }
};
</script>

<style>
  .santol {
    border: dashed black 1px;
    display: inline-block;
    margin: 10px;
    padding: 10px;
    background-color: brown;
  }

</style>