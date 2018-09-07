<template>
  <li class="list-item">
    <slot/>
  </li>
</template>

<script>
import { ElementMixin, HandleDirective } from 'vue-slicksort';

export default {
  mixins: [ElementMixin],
  props: ['item'],
  directives: { handle: HandleDirective },
};
</script>
