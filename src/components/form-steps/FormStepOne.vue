<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      validationOn: false
    }
  },
  methods: {
    validateForm() {
      this.validationOn = true;
      if (this.name && this.email && this.phone) {
        return true;
      }
      return false;
    },
    nextStep() {
      if (this.validateForm()) {
        this.$emit('setActiveTab', 2);
      }
    }
  }
}
</script>

<template>

  <div class="form-step">
    <!-- info -->
    <div class="form-step__info">
      <h2 class="title">Personal info</h2>
      <p class="text">
        Please provide your name, email address, and phone number.
      </p>
    </div>
    <!-- inputs -->
    <div class="form-step__inputs">
      <label class="form-label">Name
        <input
          :class="{error: validationOn && !name}"
          v-model="name"
          type="text"
          class="form-input"
          name="name"
          placeholder="e.g. Stephan King"
        />
        <p class="error-msg">This field is required</p>
      </label>
      <label class="form-label">Email Address
        <input
          :class="{error: validationOn && !email}"
          v-model="email"
          type="email"
          class="form-input"
          name="email"
          placeholder="e.g. stephanking@lorem.com"
        />
        <p class="error-msg">This field is required</p>
      </label>
      <label class="form-label">Phone Number
        <input
          :class="{error: validationOn && !phone}"
          v-model="phone"
          type="text"
          class="form-input"
          pattern="[0-9]+"
          name="phone"
          placeholder="e.g. +1 234 567 890"
        />
        <p class="error-msg">This field is required</p>
      </label>
    </div>
    <!-- buttons -->
    <div class="form-step__btns">
      <button class="btn" type="button" @click="nextStep">Next step</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>
@import '../../main.scss';

.form-step {
  &__inputs {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  
  &__btns {
    justify-content: end !important;
  }
}
</style>