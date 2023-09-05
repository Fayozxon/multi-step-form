<script>
import FormSidebar from './FormSidebar.vue';
import FormStepOne from './form-steps/FormStepOne.vue';
import FormStepTwo from './form-steps/FormStepTwo.vue';
import FormStepThree from './form-steps/FormStepThree.vue';
import FormStepFour from './form-steps/FormStepFour.vue';
import FormSuccessMsg from './FormSuccessMsg.vue';

export default {
  components: { FormSidebar, FormStepOne, FormStepTwo, FormStepThree, FormStepFour, FormSuccessMsg },
  data() {
    return {
        activeTab: 1,
        selectedPlan: 'arcade',
        planPrice: '90',
        selectedTime: 'yearly',
        selectedAddOns: [
          { title: 'online service', price: 10 },
          { title: 'larger storage', price: 20 },
        ]
    }
  },
  methods: {
    setActiveTab(tabNum) {
        this.activeTab = tabNum;
    },
    selectPlan(plan, price, planTime) {
      this.selectPlan = plan;
      this.planPrice = price;
      this.selectedTime = planTime;
    }
  }
}
</script>

<template>
  
    <form @submit.prevent class="form-box">

        <FormSidebar :activeTab="activeTab"></FormSidebar>

        <div class="form-box__steps">

          <FormStepOne @setActiveTab="setActiveTab" v-show="activeTab == 1"></FormStepOne>
          <FormStepTwo @setActiveTab="setActiveTab" @selectPlan="selectPlan" v-show="activeTab == 2"></FormStepTwo>
          <FormStepThree @setActiveTab="setActiveTab" v-show="activeTab == 3"></FormStepThree>
          <FormStepFour
            @setActiveTab="setActiveTab"
            v-show="activeTab == 4"
            :selectedPlan="selectedPlan"
            :planPrice="planPrice"
            :selectedTime="selectedTime"
          ></FormStepFour>
          <FormSuccessMsg v-show="activeTab == 5"></FormSuccessMsg>
          
        </div>

    </form>

</template>

<style lang="scss">
@import '../main.scss';

.form-box {
  display: grid;
  grid-template-columns: auto 1fr;
  width: 910px;
  height: 600px;
  padding: 15px !important;
  background-color: $clr-white;
  border-radius: 15px;
  box-shadow: 0 15px 30px rgba(0,0,0,0.02);

  @include media-sm {
    display: block;
    background: transparent;
    width: auto;
    height: auto;
  }

  &__steps {
    padding: 40px 80px;
    padding-bottom: 15px;

    @include media-sm {
      padding: 50px 25px;
      background: $clr-white;
      box-shadow: 0 15px 30px rgba(0,0,0,0.02);
      border-radius: 15px;
      margin-top: 100px;
      margin-bottom: 100px;
    }

    .form-step {
      position: relative;
      width: 100%;
      height: 100%;
      display: grid;
      align-content: start;
      gap: 40px;

      @include media-sm {
        position: static;
        gap: 25px;
      }
  
      &__btns {
        position: absolute;
        bottom: 15px;
        left: 0;
        right: 0;
        display: flex;
        justify-content: space-between;

        @include media-sm {
          position: fixed;
          bottom: 0;
          background: $clr-white;
          padding: 16px;
          box-shadow: 0 -15px 30px rgba(0,0,0,0.04);
          z-index: 10;
        }
      }
  
      .title {
        font-size: $fs-lg;
        font-weight: 700;
        padding-bottom: 10px;
      }
  
      .text {
        color: $clr-grey;
        font-weight: 400;
        line-height: 1.4;
      }
    }
  }
}

</style>