<template>
  <div>
    <h1>{{ part.title }}</h1>
    <div>
      {{ part.description }}
    </div>
  </div>
</template>

<script>
import getPartsMixin from './get-parts-mixin';

export default {
  name: 'PartInfo',
  mixins: [getPartsMixin],
  props: {
    partType: {
      type: String,
    },
    partId: {
      type: [String, Number],
      validator(value) {
        return Number.isInteger(+value);
      },
    },
  },
  computed: {
    part() {
      return this.parts[this.partType].find((part) => part.id === +this.partId);
    },
  },
};
</script>
