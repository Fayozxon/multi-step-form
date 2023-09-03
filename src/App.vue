<script>
import FormBox from './components/FormBox.vue';

export default {
  components: {FormBox}
}
</script>

<template>

  <main class="main">
    
    <FormBox></FormBox>

  </main>

</template>

<style lang="scss" scoped>
@import './main.scss';


.main {
  display: grid;
  place-items: center;
  min-height: 100vh;

  @include media-sm {
    place-items: unset;
    justify-content: center;
  }
}
</style>