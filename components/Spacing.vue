<template>
  <div class="columns">
    <div class="column col-12">
      <small>Remover espaços</small>
    </div>
    <div class="column col-12">
      <format-button :is-active.sync="is_remove_all_active" label="Remover Espaços"></format-button>
    </div>
  </div>
</template>

<script>
import FormatButton from "~/components/FormatButton.vue";

export default {
  props: ["input", "output"],

  data() {
    return {
      is_remove_extra_active: false,
      is_remove_all_active: false
    };
  },

  components: {
    FormatButton
  },

  methods: {
    remove_all_whitespaces: function() {
      var output = [];
      for (let i = 0; i < this.input.length; i++) {
        if (this.input[i].match(/\s/))
          continue;
        else output[i] = this.input[i];
      }

      this.$emit("update:output", output.join(''));
    },

    deactivate_all: function() {
      if (
        !this.is_remove_extra_active &&
        !this.is_remove_all_active
      )
        this.$emit("update:output", this.input);
    }
  },

  watch: {
    is_remove_extra_active(val) {
      if(val)
        this.remove_extra_whitespaces();
      else
        this.deactivate_all();
    },

    is_remove_all_active(val) {
      if(val)
        this.remove_all_whitespaces();
      else
        this.deactivate_all();
    }
  }
};
</script>
