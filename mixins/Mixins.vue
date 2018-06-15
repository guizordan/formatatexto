<script>
export default {
  methods: {
    add_format(text){
      let res = {component: this.$options._componentTag, text}
      this.$emit('add-format', res)
    },

    remove_format(component){
      this.$emit('remove-format', component)
    }
  }
}
</script>
