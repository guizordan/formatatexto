<script>
export default {
  methods: {
    add_format(text){
      let res = {component: this.$options._componentTag, text}
      console.log('adding format', res)
      this.$emit('add-format', res)
    },

    remove_format(component){
      this.$emit('remove-format', component)
    }
  }
}
</script>
