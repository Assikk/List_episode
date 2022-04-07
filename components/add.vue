<template>
  <button class="px-[20px] py-[10px] rounded bg-[#00b700] text-white"
  @click="$emit('click')">
    <slot/>
  </button>
</template>
