<template>
  <button ref="button" @click="activate" class="btn">{{label}}</button>
</template>

<script>
export default {
  data() {
    return {
      active: false
    };
  },

  props: ['label'],

  methods: {
    activate: function() {
      if (this.active) {
        this.$refs.button.classList.remove("active");
        this.$emit("deactivate", input);
        this.active = false;
      } else {
        this.$refs.button.classList.add("active");
        this.$emit("activate");
        this.active = true;
      }
    }
  }
};
</script>
