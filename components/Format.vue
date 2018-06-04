<template>
  <button @click="format" class="btn btn-block">
    Formatar Texto!
  </button>
</template>

<script>
export default {
  props: ['input', 'output'],

  methods: {
    format: function() {
      var formatted = this.remove_extra_whitespaces(this.input);
      formatted = this.deal_with_dots(formatted);
      this.$emit('update:output', formatted);
      this.$emit('update:input', formatted);
    },

    remove_extra_whitespaces: function(string) {
      var output = [];
      for (let i = 0; i < string.length; i++) {
        if (string[i].match(/\s/) && string[i + 1].match(/\s/)) continue;
        else output[i] = string[i];
      }

      return output.join('');
    },

    deal_with_dots: function(string) {
      var output = [];
      return string.replace(/\.[a-zA-Z]/g, function(substring){
        return '. ' + substring[1].toUpperCase();
      });

      console.log(string);
    }
  }
};
</script>
