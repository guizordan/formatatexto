<template>
<div class="column col-12">
  <div class="column col-12">
    <div class="form-group">
      <textarea v-model="input" class="form-input" rows="5"></textarea>
    </div>
  </div>

  <div class="column col-12 text-center">
    <format :input="input" :previous-output.sync="previousOutput" :output.sync="output"></format>
  </div>

  <div class="column col-12 mt-2 mb-2">
    <strong>Mais Opções</strong>

    <div class="columns">
      <div class="column col-4 col-md-12">
        <capitalize @remove-format="removeFormat" @add-format="addFormat" :text="output || input"></capitalize>
      </div>

      <div class="column col-4 col-md-12">
        <reverse :previous-output="previousOutput" :output.sync="formats[formats.length-1].val || ''"></reverse>
      </div>

    </div>
  </div>

  <div class="column col-12">
    <output-text-area :output.sync="formats[formats.length-1].val || ''"></output-text-area>
  </div>
</div>
</template>

<script>
import Capitalize from '~/components/Capitalize.vue';
import Format from '~/components/Format.vue';
import OutputTextArea from '~/components/OutputTextArea.vue';
import Reverse from '~/components/Reverse.vue';

export default {
  components: {
    Capitalize,
    Format,
    Reverse,
    OutputTextArea
  },

  data() {
    return {
      formats: [{val: '', component: ''}],
      input: '  testando.string    aaaaaa',
      output: ''
    };
  },

  methods: {
    addFormat(payload){
      this.formats.push(payload)
      console.log(this.formats)
    },

    removeFormat(payload){
      console.log(payload)
    },
  },

}
</script>
