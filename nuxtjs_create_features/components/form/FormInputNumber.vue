<template>
  <input v-model="componentValue" maxlength="16" />
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      required: true
    },
    displayZeroValue: {
      type: Boolean,
      default: () => false
    },
    acceptFloatPoint: {
      type: Boolean,
      default: () => false
    }
  },
  computed: {
    componentValue: {
      get() {
        return this.value ? this.value : this.displayZeroValue ? 0 : "";
      },
      set(newValue) {
        const inputValue = Number(newValue);
        const action = { value: inputValue };
        const isDotEnter = inputValue === this.value;
        if (isDotEnter && !this.acceptFloatPoint) {
          this.$forceUpdate();
          return;
        }
        if (inputValue === 0) {
          this.$emit("input", action);
          this.$forceUpdate();
          return;
        }
        if (!inputValue) {
          this.$forceUpdate();
          return;
        }
        this.$emit("input", action);
      }
    }
  }
};
</script>
