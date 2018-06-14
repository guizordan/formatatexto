<template>
  <button @click="format" class="btn btn-block btn-success">
    Formatar Texto!
  </button>
</template>

<script>
import Mixins from '~/mixins/Mixins.vue';

export default {
  props: ['text'],

  mixins: [Mixins],

  methods: {
    format: function() {
      var formatted;
      formatted = this.remove_extra_whitespaces(this.text);
      formatted = this.capitalize_first_letter(formatted);
      formatted = this.deal_with_dots(formatted);

      this.add_format(formatted, 'format');
    },

    remove_extra_whitespaces: function(string) {
      var output = [];
      for (let i = 0; i < string.length; i++) {
        if (string[i].match(/\s/) && string[i + 1].match(/\s/)) continue;
        else output[i] = string[i];
      }
      output = output.join('');

      return output.trim();
    },

    capitalize_first_letter: function(string) {
      if (!string.match(/[A-Z]/)) {
        return string.replace(/[a-z]/, function(substring) {
          return substring.toUpperCase();
        });
      }
    },

    deal_with_dots: function(string) {
      return string.replace(/\.[a-zA-Z]/g, function(substring) {
        return '. ' + substring[1].toUpperCase();
      });
    }
  }
};
</script>
