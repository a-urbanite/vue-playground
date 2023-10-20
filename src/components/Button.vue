<template>
  <button
    @click="$emit('btn-click')"
    :style="{ background: btnColor }"
    class="btn"
  >
    {{ btnText }}
  </button>
</template>

<script>
export default {
  name: "HeaderButton",
  props: {
    btnText: String,
    btnColor: String,
  },
  emits: ["btn-click"],
};
</script>
