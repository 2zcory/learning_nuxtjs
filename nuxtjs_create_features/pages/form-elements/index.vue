<template>
  <div class="container">
    <form-input-number
      :value="inputNumberData || 0"
      @input="inputNumberData = $event.value"
    />
  </div>
</template>

<script>
import FormInputNumber from "~/components/form/FormInputNumber";

export default {
  components: {
    FormInputNumber
  },
  data() {
    return {
      inputNumberData: null
    };
  }
};
</script>
