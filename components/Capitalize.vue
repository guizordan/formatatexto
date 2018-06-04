<template>
  <div class="columns">
    <div class="column col-12">
      <small>Capitalização</small>
    </div>
    <div class="column col-12">
      <format-button :is-active.sync="is_upcase_active" label="AAA"></format-button>
      <format-button :is-active.sync="is_downcase_active" label="aaa" class="ml-2"></format-button>
      <format-button :is-active.sync="is_emocase_active" label="aAa" class="ml-2"></format-button>
    </div>
  </div>
</template>

<script>
import FormatButton from '~/components/FormatButton.vue';

export default {
  props: ['input', 'output'],

  data() {
    return {
      is_upcase_active: false,
      is_downcase_active: false,
      is_emocase_active: false
    };
  },

  components: {
    FormatButton
  },

  methods: {
    activate_upcase: function() {
      this.$emit('update:output', this.input.toUpperCase());
    },

    activate_downcase: function() {
      this.$emit('update:output', this.input.toLowerCase());
    },

    activate_emocase: function() {
      var output = [];
      for (let i = 0; i < this.input.length; i++) {
        if (i % 2 == 0) output[i] = this.input[i].toLowerCase();
        else output[i] = this.input[i].toUpperCase();
      }
      this.$emit('update:output', output.join(''));
    },

    deactivate_all: function() {
      if (
        !this.is_upcase_active &&
        !this.is_downcase_active &&
        !this.is_emocase_active
      )
        this.$emit('update:output', this.input);
    }
  },

  watch: {
    is_upcase_active(val) {
      if (val) {
        this.is_emocase_active = false;
        this.is_downcase_active = false;
        this.activate_upcase();
      } else {
        this.deactivate_all();
      }
    },

    is_downcase_active(val) {
      if (val) {
        this.is_emocase_active = false;
        this.is_upcase_active = false;
        this.activate_downcase();
      } else {
        this.deactivate_all();
      }
    },

    is_emocase_active(val) {
      if (val) {
        this.is_upcase_active = false;
        this.is_downcase_active = false;
        this.activate_emocase();
      } else {
        this.deactivate_all();
      }
    }
  }
};
</script>
