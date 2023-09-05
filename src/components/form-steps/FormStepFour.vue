<script>
export default {
  props: ['selectedPlan', 'planPrice', 'selectedTime']
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
    <div class="form-step__full-info">
      <div class="item">
        <h3 class="plan">{{ selectedPlan }} ({{ selectedTime }})
          <span @click="$emit('setActiveTab', 2)">Change</span>
        </h3>
        <h3 class="plan-price">${{ planPrice }}/yr</h3>
      </div>
      <div class="line"></div>
      <div class="item">
        <h3 class="heading">Online Service</h3>
        <h3 class="price">+$10/yr</h3>
      </div>
      <div class="item">
        <h3 class="heading">Larger Storage</h3>
        <h3 class="price">+$20/yr</h3>
      </div>
    </div>
    <div class="form-step__total">
      <h3 class="heading">Total (per year)</h3>
      <h3 class="price">$120/yr</h3>
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

.form-step__full-info {
  background: $clr-bg-300;
  padding: 20px 25px;
  border-radius: 10px;
  text-transform: capitalize;

  .item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 0;

    .heading {
      font-weight: 300;
      color: $clr-grey;
    }

    .price {
      font-weight: 300;
      text-transform: lowercase;
    }
  }

  .line {
    width: 100%;
    height: 1px;
    background: $clr-lt-grey;
    opacity: 0.5;
    margin: 25px 0;
  }

  .plan {
    font-weight: 700;

    &-price {
      font-weight: 700;
      text-transform: lowercase;
    }

    span {
      text-decoration: underline;
      display: block;
      font-weight: 300;
      cursor: pointer;
      color: $clr-grey;
      font-size: $fs-sm;
      padding-top: 3px;
      transition: $ts-200;

      &:hover {
        color: $clr-purple-200;
      }
    }
  }
}

.form-step__total {
  display: flex;
  justify-content: space-between;
  padding: 0 25px;
  text-transform: capitalize;

  .heading {
    color: $clr-grey;
  }

  .price {
    font-weight: 700;
    color: $clr-purple-200;
    font-size: 24px;
    text-transform: lowercase;
  }
}

</style>