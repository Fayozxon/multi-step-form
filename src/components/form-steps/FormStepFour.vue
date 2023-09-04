<script>
export default {
  
}
</script>

<template>
  
  <div class="form-step">
    <!-- info -->
    <div class="form-step__info">
      <h2 class="title">Finishing up</h2>
      <p class="text">
        Double-check everything looks OK before confirming.
      </p>
    </div>

    <!-- buttons -->
    <div class="form-step__btns">
      <button type="button" class="btn btn-inline" @click="$emit('setActiveTab', 3)">Go back</button>
      <button class="btn btn-accent" type="submit" @submit.prevent @click="$emit('setActiveTab', 5)">Confirm</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>
@import '../../main.scss';

</style>