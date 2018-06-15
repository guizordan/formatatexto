<template>
  <div class="columns">
    <div class="column col-12">
      <small>Capitalizar</small>
    </div>
    <div class="column col-12">
      <format-button :is-active.sync="is_upcase_active" label="AAA"></format-button>
      <format-button :is-active.sync="is_downcase_active" label="aaa" class="ml-2"></format-button>
      <format-button :is-active.sync="is_emocase_active" label="aAa" class="ml-2"></format-button>
    </div>
  </div>
</template>

<script>
import FormatButton from '~/components/FormatButton.vue'
import Mixins from '~/mixins/Mixins.vue'

export default {
  props: ['text'],

  mixins: [Mixins],

  data() {
    return {
      is_upcase_active: false,
      is_downcase_active: false,
      is_emocase_active: false
    }
  },

  components: {
    FormatButton
  },

  methods: {
    activate_upcase: function() {
      this.add_format(this.text.toUpperCase())
    },

    activate_downcase: function() {
      this.add_format(this.text.toLowerCase())
    },

    activate_emocase: function() {
      let newText = []
      for (let i = 0; i < this.text.length; i++) {
        if (i % 2 == 0) newText[i] = this.text[i].toLowerCase()
        else newText[i] = this.text[i].toUpperCase()
      }

      this.add_format(newText.join(''))
    },

    deactivate_all: function() {
      if (
        !this.is_upcase_active &&
        !this.is_downcase_active &&
        !this.is_emocase_active
      )
        this.remove_format('capitalize')
    }
  },

  watch: {
    is_upcase_active(val) {
      if (val) {
        this.is_emocase_active = false
        this.is_downcase_active = false
        this.activate_upcase()
      } else {
        this.deactivate_all()
      }
    },

    is_downcase_active(val) {
      if (val) {
        this.is_emocase_active = false
        this.is_upcase_active = false
        this.activate_downcase()
      } else {
        this.deactivate_all()
      }
    },

    is_emocase_active(val) {
      if (val) {
        this.is_upcase_active = false
        this.is_downcase_active = false
        this.activate_emocase()
      } else {
        this.deactivate_all()
      }
    }
  }
};
</script>
