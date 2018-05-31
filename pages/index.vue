<template>

<div class="container mt-2">
  <div class="columns">
    <div class="column col-sm-12 col-6 col-ml-auto col-mr-auto">
        
      <div class="columns">

        <div class="column col-12 mb-2">
          <h1>Formatar Texto</h1>
          <div class="form-group">
              <textarea v-model="input" class="form-input" rows="5"></textarea>
          </div>
        </div>

        
        <capitalize :input="input" :output.sync="output"></capitalize>

        <!-- <format-button @deactivate="previous_value" @activate="remove_whitespaces" 
        :original_value="input" label="Remove Espaços" class="ml-2"></format-button> -->

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
import FormatButton from "~/components/FormatButton.vue"
import Capitalize from "~/components/Capitalize.vue"

export default {
  components: {
    FormatButton,
    Capitalize
  },

  data() {
    return {
      input: 'Testando String',
      output: ''
    };
  },

  mounted() {
    // console.log(this.$refs);
  },

  methods: {

    remove_whitespaces: function() {
      var output = [];
      for (let i = 0; i < this.input.length; i++) {
        if (this.input[i].match(/\s/) && this.input[i + 1].match(/\s/))
          continue;
        else output[i] = this.input[i];
      }

      this.output = output.join("");
    },

    previous_value: function(prev_val){
      console.log(prev_val);
      this.output = prev_val;
    }
  }
};
</script>
