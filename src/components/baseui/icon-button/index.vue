<template>
  <div class="icon-button" @click="buttonClick">
    <div class="icon-bg">
      <svg-icon :icon-class="icon" class-name="icon"></svg-icon>    
    </div>
    <div class="title">{{ title }}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: "IconButton",
  props:{
    index: {
      type: Number,
      default: 0
    },
    icon: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
  emits:['item-click'],
  setup (props, context) {
    const buttonClick = () => {
      context.emit('item-click', props.index)
    }
    return {
      buttonClick
    }
  }
})
</script>

<style scoped lang="scss">
.icon-button {
  height: 1.5rem;
  width: 1rem;
  .icon-bg {
    height: 1rem;
    width: 1rem;
    text-align: center;
    line-height: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(100, 0, 0, 0.1);
    border-radius: 50%;
  }
  .title {
    margin-top: .2rem;
    color: black;
    font-size: 0.24rem;
    text-align: center;
  }
  .icon {
    font-size: .6rem;
  }
}
</style>