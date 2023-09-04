<script>
export default {
  data() {
    return {
      selectedPlan: 1,
      selectedYearlyPay: true
    }
  }
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
        <div class="card" :class="{active: selectedPlan == 1}" @click="selectedPlan = 1">
          <img src="../../assets/icon-arcade.svg" class="card__img" aria-hidden="true" alt="">
          <div class="card__right">
            <h3 class="card__title">Arcade</h3>
            <h3 class="card__price" v-if="selectedYearlyPay">$90/yr</h3>
            <h3 class="card__price" v-else>$9/mo</h3>
            <h3 class="card__info" :class="{show: selectedYearlyPay}">2 months free</h3>
          </div>
        </div>
        <div class="card" :class="{active: selectedPlan == 2}" @click="selectedPlan = 2">
          <img src="../../assets/icon-advanced.svg" class="card__img" aria-hidden="true" alt="">
          <div class="card__right">
            <h3 class="card__title">Advanced</h3>
            <h3 class="card__price" v-if="selectedYearlyPay">$120/yr</h3>
            <h3 class="card__price" v-else>$12/mo</h3>
            <h3 class="card__info" :class="{show: selectedYearlyPay}">2 months free</h3>
          </div>
        </div>
        <div class="card" :class="{active: selectedPlan == 3}" @click="selectedPlan = 3">
          <img src="../../assets/icon-pro.svg" class="card__img" aria-hidden="true" alt="">
          <div class="card__right">
            <h3 class="card__title">Pro</h3>
            <h3 class="card__price" v-if="selectedYearlyPay">$150/yr</h3>
            <h3 class="card__price" v-else>$15/mo</h3>
            <h3 class="card__info" :class="{show: selectedYearlyPay}">2 months free</h3>
          </div>
        </div>
      </div>
    </div>
    <div class="form-step__toggle">
      <h3 class="option" :class="{active: !selectedYearlyPay}">Monthly</h3>
      <div class="form-toggle" @click="selectedYearlyPay = !selectedYearlyPay">
        <input type="checkbox" checked>
        <span class="custom"></span>
      </div>
      <h3 class="option" :class="{active: selectedYearlyPay}">Yearly</h3>
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

      @include media-sm {
        grid-template-columns: 1fr;
      }

      .card {
        display: flex;
        align-items: start;
        flex-direction: column;
        justify-content: space-between;
        border: 1px solid $clr-lt-grey;
        border-radius: 10px;
        padding: 20px 15px;
        height: 175px;
        transition: $ts-200;
        cursor: pointer;

        @include media-sm {
          flex-direction: row;
          justify-content: start;
          gap: 20px;
          height: unset;

          &__right {
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
          }
        }

        &.active {
          background: $clr-bg-300;
          border-color: $clr-purple-200;
        }

        &__title {
          font-weight: 700;
        }

        &__price {
          color: $clr-grey;
          padding: 3px 0;
        }

        &__info {
          font-size: fs-sm;
          display: none;

          &.show {
            display: inline-block;
          }
        }
      }
    }
  }

  &__toggle {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    padding: 20px 0;
    background: $clr-bg-300;
    border-radius: 10px;

    .option {
      font-weight: 700;
      color: $clr-grey;
      transition: $ts-200;

      &.active {
        color: $clr-dk-blue;
      }
    }
  }
}

</style>