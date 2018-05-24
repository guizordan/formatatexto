<template>

<div class="container mt-2">
  <div class="columns mb-2">
    <div class="column col-6 col-ml-auto col-mr-auto">
        <h1>Formatar Texto</h1>
        <div class="form-group">
            <textarea v-model="input" class="form-input" rows="5"></textarea>
        </div>

        <button @click="upcase" class="btn">Capitalizar</button>
        <button @click="downcase" class="btn ml-2">Minimizar</button>
    </div>

  </div>

    <div class="columns">
    <div class="column col-6 col-ml-auto col-mr-auto">
        <div class="form-group">
            <textarea v-model="output" class="form-input" rows="5"></textarea>
        </div>
    </div>

  </div>

</div>


</template>

<script>
import AppLogo from '~/components/AppLogo.vue'

export default {
    data(){
        return{
            input: null,
            output: null
        }
    },

    methods: {
        upcase: function(){
            console.log('method');
            this.output = this.input.toUpperCase();
        },

        downcase: function(){
            console.log('method');
            this.output = this.input.toLowerCase();
        }
    }

}
</script>
