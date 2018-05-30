<template>
  <button @click="toggle" :class="{active : 'active'}" class="btn">{{label}}</button>
</template>

<script>
export default {
  props: ['original_value', 'label'],

  data() {
    return {
      active: false,
      previous_value: this.original_value
    };
  },

  methods: {
    toggle: function() {
      if (this.active) {
        this.$emit("deactivate", this.previous_value);
        this.active = false;
      } else {
        this.previous_value = this.original_value;
        this.$emit("activate");
        this.active = true;
      }
    }
  }

  ,watch:{
    original_value(val){
      this.previous_value = val;
    }
  }
  
};
</script>
