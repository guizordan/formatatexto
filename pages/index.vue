<template>

<div class="container mt-2">
  <div class="columns">
    <div class="column col-sm-12 col-6 col-ml-auto col-mr-auto">
        
      <div class="columns">
        
        <div class="column col-12">
          <h1>Formata Texto</h1>
          <div class="form-group">
              <textarea v-model="input" class="form-input" rows="5"></textarea>
          </div>
        </div>

        <div class="column col-12">

          <div class="columns mb-2">
            <div class="column col-4">
              <capitalize :input="input" :output.sync="output"></capitalize>
            </div>

            <div class="column col-8">
              <spacing :input="input" :output.sync="output"></spacing>
            </div>
          </div>

        </div>

        <div class="column col-12">
          <div class="form-group">
            <textarea v-model="output" class="form-input" rows="5"></textarea>
          </div>
        </div>

      </div>
    </div>

  </div>
</div>

</template>

<script>
import Capitalize from "~/components/Capitalize.vue"
import Spacing from "~/components/Spacing.vue"

export default {
  components: {
    Capitalize,
    Spacing
  },

  data() {
    return {
      input: 'Testando String',
      output: ''
    };
  },

  mounted() {
    // console.log(this.$refs);
  }
};
</script>
