<template>
  <div class="column col-12 mb-2">
      <format-button :is-active.sync="is_upcase_active" label="Capitalizar"></format-button>
      
      <format-button :is-active.sync="is_downcase_active" label="Minimizar" class="ml-2"></format-button>
  </div>
</template>

<script>
import FormatButton from "~/components/FormatButton.vue";

export default {
  props: ["input", "output"],

  data() {
    return {
      is_upcase_active: false,
      is_downcase_active: false,
      previous_output: this.input
    };
  },

  components: {
    FormatButton
  },

  methods: {
    activate_upcase: function(active) {
      this.$emit('update:output', this.input.toUpperCase());
    },

    activate_downcase: function(active) {
      this.$emit('update:output', this.input.toLowerCase());
    },

    deactivate_upcase: function(){
      if(this.is_upcase_active){
        this.is_upcase_active = false;
        this.$emit('update:output', this.previous_output || this.input);
      }
    },

    deactivate_downcase: function(){
      if(this.is_downcase_active){
        this.is_downcase_active = false;
        this.$emit('update:output', this.previous_output || this.input);
      }
    }
  },

  watch: {
    is_upcase_active(val){
      if(val){
        this.deactivate_downcase();
        this.activate_upcase();
      } else
        this.deactivate_upcase();
    },

    is_downcase_active(val){
      if(val){
        this.deactivate_upcase();
        this.activate_downcase();
      } else
        this.deactivate_downcase();
    }
  }
};
</script>
