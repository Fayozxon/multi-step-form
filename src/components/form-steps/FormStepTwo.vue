<script>
export default {
  
}
</script>

<template>
  
  <div class="form-step">
    <!-- info -->
    <div class="form-step__info">
      <h2 class="title">Select your plan</h2>
      <p class="text">
        You have the option of monthly or yearly billing.
      </p>
    </div>
    <!-- plans -->
    <div class="form-step__plans">
      <div class="form-step__plans--cards">
        <div class="card">
          <div class="card__img">
            <img src="../../assets/icon-arcade.svg" aria-hidden="true" alt="">
          </div>
          <h3 class="card__title">Arcade</h3>
        </div>
      </div>
    </div>
    <!-- buttons -->
    <div class="form-step__btns">
      <button type="button" class="btn btn-inline" @click="$emit('setActiveTab', 1)">Go back</button>
      <button class="btn" type="button" @click="$emit('setActiveTab', 3)">Next step</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>
@import '../../main.scss';

.form-step {
  &__plans {
    &--cards {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 16px;

      .card {
        height: 200px;
        border: 1px solid $clr-lt-grey;
        border-radius: 10px;

        &__img {
          background: red;
        }
      }
    }
  }
}

</style>