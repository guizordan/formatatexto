<template>
<div class="column col-12">
  <div class="column col-12">
    <div class="form-group">
      <textarea v-model="input" class="form-input" rows="5"></textarea>
    </div>
  </div>

  <div class="column col-12 text-center">
    <format @add-format="addFormat" :text="text">></format>
  </div>

  <div class="column col-12 mt-2 mb-2">
    <strong>Mais Opções</strong>

    <div class="columns">
      <div class="column col-4 col-md-12">
        <capitalize @remove-format="removeFormat" @add-format="addFormat" :text="text"></capitalize>
      </div>

      <div class="column col-4 col-md-12">
        <reverse @remove-format="removeFormat" @add-format="addFormat" :text="text"></reverse>
      </div>

    </div>
  </div>

  <div class="column col-12 mt-2 mb-2">
    {{formats}}
  </div>

  <div class="column col-12">
    <output-text-area :output="text"></output-text-area>
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
      formats: [],
      input: '  testando.string    aaaaaa'
    };
  },

  methods: {
    addFormat(payload) {
      console.log(payload, 'payload')
      let exists = this.formats.findIndex(format => { return payload.component == format.component})
      if(exists > -1){
        console.log(exists)
        this.formats[exists].text = payload.text
      } else{
        this.formats.push(payload)
      }
    },

    removeFormat(payload) {
      console.log(payload);
    }
  },

  computed: {
    text(){
      let newFormat = this.formats[this.formats.length - 1];
      return newFormat && newFormat.text ? newFormat.text : this.input;
    },
  },
};
</script>
