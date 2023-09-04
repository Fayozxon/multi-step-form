<script>
export default {
  data() {
    return {
      onlineService: true,
      cloudService: true,
      customizationService: false
    }
  }
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
    <div class="form-step__cards">
      <label class="card" :class="{active: onlineService}">
        <div class="form-checkbox">
          <input type="checkbox" v-model="onlineService">
          <span class="custom"></span>
        </div>
        <div class="card__info">
          <h3 class="title">Online service</h3>
          <h3 class="text">Access to multiplayer games</h3>
        </div>
        <h3 class="card__price">+$10/yr</h3>
      </label>
      <label class="card" :class="{active: cloudService}">
        <div class="form-checkbox">
          <input type="checkbox" v-model="cloudService">
          <span class="custom"></span>
        </div>
        <div class="card__info">
          <h3 class="title">Larger storage</h3>
          <h3 class="text">Extra 1TB of cloud save</h3>
        </div>
        <h3 class="card__price">+$20/yr</h3>
      </label>
      <label class="card" :class="{active: customizationService}">
        <div class="form-checkbox">
          <input type="checkbox" v-model="customizationService">
          <span class="custom"></span>
        </div>
        <div class="card__info">
          <h3 class="title">Customizable profile</h3>
          <h3 class="text">Custom theme on your profile</h3>
        </div>
        <h3 class="card__price">+$20/yr</h3>
      </label>
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

.form-step {
  &__cards {
    display: flex;
    flex-direction: column;
    gap: 20px;

    .card {
      display: grid;
      align-items: center;
      grid-template-columns: 1fr 9fr 1fr;
      gap: 10px;
      padding: 15px;
      border: 1px solid $clr-lt-grey;
      border-radius: 10px;
      transition: $ts-200;
      cursor: pointer;

      &.active {
        border-color: $clr-purple-200;
        background-color: $clr-bg-300;
      }

      &__info {
        .title {
          font-size: $fs-md;
          padding-bottom: 3px;
          font-weight: 500;
        }

        .text {
          font-size: $fs-sm;
        }
      }

      &__price {
        color: $clr-purple-200;
        font-weight: 500;
      }
    }
  }
}

</style>