<template>
  <button @click="toggle" :class="{'active' : isActive}" class="btn">{{label}}</button>
</template>

<script>
export default {
  props: ['label', 'isActive'],

  methods: {
    toggle: function() {
      this.$emit('update:isActive', !this.isActive);
    }
  }
};
</script>
