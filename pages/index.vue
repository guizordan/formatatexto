<template>

<div class="container mt-2">
  <div class="columns">
    <div class="column col-6 col-xl-6 col-lg-6 col-md-8 col-sm-12 col-xs-12 col-mx-auto">
        
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

        <div class="column col-12 mb-2">
          <strong>Mais Opções</strong>

          <div class="columns">
            <div class="column col-4 col-sm-12">
              <capitalize :input="input" :output.sync="output"></capitalize>
            </div>

            <div class="column col-4 col-sm-12">
              <capitalize :input="input" :output.sync="output"></capitalize>
            </div>

          </div>
        </div>

        <div class="column col-12">
          <Output-text-area :input="input" :output.sync="output"></Output-text-area>
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
import OutputTextArea from '~/components/OutputTextArea.vue';

export default {
  components: {
    Capitalize,
    Spacing,
    Format,
    OutputTextArea
  },

  data() {
    return {
      input: '  testando.string    aaaaaa',
      output: ''
    };
  },

  mounted() {
    // console.log(this.$refs);
  }
};
</script>
