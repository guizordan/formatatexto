<script>
export default {
  methods: {
    add_format(val, component){
      let res = {component, val}
      console.log('adding format', res)
      this.$emit('add-format', res)
    },

    remove_format(component){
      this.$emit('remove-format', component)
    }
  }
}
</script>
