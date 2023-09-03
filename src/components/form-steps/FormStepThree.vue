<script>
export default {
  
}
</script>

<template>
  
  <div class="form-step">
    <!-- info -->
    <div class="form-step__info">
      <h2 class="title">Pick add-ons</h2>
      <p class="text">
        Add-ons help enhance your gaming experience.
      </p>
    </div>
    
    <!-- buttons -->
    <div class="form-step__btns">
      <button type="button" class="btn btn-inline" @click="$emit('setActiveTab', 2)">Go back</button>
      <button class="btn" type="button" @click="$emit('setActiveTab', 4)">Next step</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>
@import '../../main.scss';

</style>