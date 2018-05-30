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

        <div class="column col-12 mb-2">
          <button ref="upcase" @click="upcase" class="btn">Capitalizar</button>
          <button ref="downcase" @click="downcase" class="btn ml-2">Minimizar</button>
          <button ref="remove_whitespaces" @click="remove_whitespaces" class="btn ml-2">Remove Espaços</button>
          <format-button label="botao"></format-button>
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
import FormatButton from "~/components/FormatButton.vue"

export default {
  data() {
    return {
      input: null,
      output: null
    };
  },

  components: {
    FormatButton
  },

  mounted() {
    console.log(this.$refs);
  },

  methods: {
    upcase: function() {
      this.output = this.input.toUpperCase();
    },

    downcase: function() {
      this.output = this.input.toLowerCase();
    },

    remove_whitespaces: function() {
      var output = [];
      for (let i = 0; i < this.input.length; i++) {
        if (this.input[i].match(/\s/) && this.input[i + 1].match(/\s/))
          continue;
        else output[i] = this.input[i];
      }

      this.output = output.join("");
      this.$refs.remove_whitespaces.classList.add("active");
    }
  }
};
</script>
