<script>
export default {
  props: ['activeTab'],
  data() {
    return {
      sidebarItems: [
        { num: 1, title: 'Your info' },
        { num: 2, title: 'Select plan' },
        { num: 3, title: 'Add-ons' },
        { num: 4, title: 'Summary' }
      ]
    }
  }
}
</script>

<template>

  <ul class="sidebar">
    <li
      v-for="item in sidebarItems"
      class="sidebar__item"
    >
      <span class="sidebar__item--number" :class="{active: activeTab == item.num}">{{ item.num }}</span>
      <div class="sidebar__item--info">
        <span class="title">Step {{ item.num }}</span>
        {{ item.title }}
      </div>
    </li>
  </ul>

</template>

<style lang="scss" scoped>
@import '../main.scss';

.sidebar {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 30px;
  width: 275px;
  height: 100%;
  padding: 40px 30px;
  background: {
    image: url('../assets/bg-sidebar-desktop.svg');
    size: cover;
    repeat: no-repeat;
  }
  border-radius: 10px;
  color: $clr-white;
  text-transform: uppercase;
  font-weight: 500;
  letter-spacing: 1.2px;
  font-size: $fs-sm;

  &__item {
    display: flex;
    align-items: center;
    gap: 15px;

    &--number {
      user-select: none;
      display: inline-block;
      width: 35px;
      height: 35px;
      text-align: center;
      line-height: 33px;
      border: 1px solid $clr-white;
      border-radius: 50%;
      transition: $ts-200;

      &.active {
        background-color: $clr-bg-200;
        border-color: $clr-bg-200;
        color: $clr-dk-blue;
      }
    }

    .title {
      font-weight: 300;
      opacity: 0.7;
    }

    &--info {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }
  }

  @include media-sm {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    height: 170px;
    border-radius: 0;
    background-image: url('../assets/bg-sidebar-mobile.svg');
    z-index: -1;
    flex-direction: row;
    justify-content: center;
    align-items: flex-start;
    gap: 15px;

    &__item {
      &--info, .title {
        display: none;
      }
    }
  }
}
</style>