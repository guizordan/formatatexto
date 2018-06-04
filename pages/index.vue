<template>

<div class="container mt-2">
  <div class="columns">
    <div class="column col-4 col-xl-8 col-lg-6 col-md-10 col-sm-12 col-mx-auto">
        
      <div class="columns">
        
        <div class="column col-12">
          <h1>Formata Texto</h1>
          <div class="form-group">
              <textarea v-model="input" class="form-input" rows="5"></textarea>
          </div>
        </div>

        <div class="column col-12 text-center">
          <format :input.sync="input" :output.sync="output"></format>
        </div>

        <div class="column col-12 mt-3 mb-2">
          <strong>Mais Opções</strong>

          <div class="columns">
            <div class="column col-3 col-lg-6 col-sm-12">
              <capitalize :input="input" :output.sync="output"></capitalize>
            </div>

          </div>
        </div>

        <div class="column col-12">
          <div class="form-group">
            <textarea v-model="output" class="form-input" rows="5"></textarea>
            <button :disabled="output.length == 0" class="btn btn-block btn-success">Copiar</button>
          </div>
        </div>

      </div>
    </div>

  </div>
</div>

</template>

<script>
import Capitalize from '~/components/Capitalize.vue';
import Spacing from '~/components/Spacing.vue';
import Format from '~/components/Format.vue';

export default {
  components: {
    Capitalize,
    Spacing,
    Format
  },

  data() {
    return {
      input: 'Testando.string',
      output: ''
    };
  },

  mounted() {
    // console.log(this.$refs);
  }
};
</script>
