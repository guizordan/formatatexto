<template>
<div class="form-group">
  <textarea ref="output" readonly v-model="output" class="form-input" rows="5"></textarea>
  <button @click="copy" :disabled="output.length == 0" class="btn btn-block btn-success">
    {{ copy_label }}
  </button>
</div>
</template>

<script>
export default {
  props: ['output'],

  data() {
    return {
      copy_label: 'Copiar'
    };
  },

  methods: {
    copy: function() {
      var self = this;;
      this.$refs.output.select();
      document.execCommand("copy");
      this.copy_label = 'Copiado!'
      
      setInterval(function(){ 
        self.copy_label = 'Copiar';
      }, 2000);
    }
  }
};
</script>
