<template>
  <div>
    <p id="amt-value">{{ inBRL }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed, toRefs } from 'vue';

export default defineComponent({
  props: {
    value: {
      type: Number,
      required: true,
    },
  },
  setup(props) {
    const { value } = toRefs(props);
    const toBRL = (value: number): string => {
      return new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' }).format(value);
    };

    const inBRL = computed(() => {
      return toBRL(value.value);
    });
    return { inBRL };
  },
});
</script>

<style scoped>
#amt-value {
  font-size: 1.25rem;
}
</style>
