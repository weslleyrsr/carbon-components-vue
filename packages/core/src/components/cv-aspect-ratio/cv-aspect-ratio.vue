<template>
  <div :class="[`${carbonPrefix}--aspect-ratio`, `${carbonPrefix}--aspect-ratio--${ratio}`]"><slot /></div>
</template>

<script>
import { carbonPrefixMixin } from '../../mixins';

export const ratios = ['16x9', '9x16', '2x1', '1x2', '4x3', '3x4', '1x1'];
export default {
  name: 'CvAspectRatio',
  mixins: [carbonPrefixMixin],
  props: {
    ratio: {
      type: String,
      validator: val => {
        const result = ratios.includes(val);
        if (!result) {
          console.warn(`Invalid options supplied to "CvAspectRation"-"${val}".`);
        }
        return result;
      },
      required: true,
    },
  },
};
</script>

<style lang="scss"></style>
