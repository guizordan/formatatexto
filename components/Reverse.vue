<template>
  <div class="columns">
    <div class="column col-12">
      <small>Inverter</small>
    </div>
    <div class="column col-12">
      <format-button :is-active.sync="is_flip_active" :label="flip_label"></format-button>
      <format-button :is-active.sync="is_mirror_active" :label="mirror_label" class="ml-2"></format-button>
    </div>
  </div>
</template>

<script>
import FormatButton from '~/components/FormatButton.vue';

export default {
  props: ['output', 'previousOutput'],

  data() {
    return {
      flip_label: '\u0250\u0250\u0250',
      mirror_label: 'texto'
        .split('')
        .reverse()
        .join(''),
      flipTable: {
        a: '\u0250',
        b: 'q',
        c: '\u0254',
        d: 'p',
        e: '\u01DD',
        f: '\u025F',
        g: '\u0183',
        h: '\u0265',
        i: '\u0131',
        j: '\u027E',
        k: '\u029E',
        l: '\u0283',
        m: '\u026F',
        n: 'u',
        r: '\u0279',
        t: '\u0287',
        v: '\u028C',
        w: '\u028D',
        y: '\u028E',
        '.': '\u02D9',
        '[': ']',
        '(': ')',
        '{': '}',
        '?': '\u00BF',
        '!': '\u00A1',
        "'": ',',
        '<': '>',
        _: '\u203E',
        ';': '\u061B',
        '\u203F': '\u2040',
        '\u2045': '\u2046',
        '\u2234': '\u2235',
        '\r': '\n'
      },

      is_flip_active: false,
      is_mirror_active: false
    };
  },

  components: {
    FormatButton
  },

  methods: {
    flip() {
      let result = this.flipString(this.previousOutput.toLowerCase());
      this.$emit('update:output', result);
    },

    mirror() {
      this.$emit(
        'update:output',
        this.previousOutput
          .split('')
          .reverse()
          .join('')
      );
    },

    deactivate_all: function() {
      if (!this.is_flip_active && !this.is_mirror_active)
        this.$emit('update:output', this.previousOutput);
    },

    flipString(aString) {
      var last = aString.length - 1;
      var result = new Array(aString.length);
      for (var i = last; i >= 0; --i) {
        let c = aString.charAt(i);
        let r = this.flipTable[c];
        result[last - i] = r != undefined ? r : c;
      }
      return result.join('');
    }
  },

  watch: {
    is_flip_active(val) {
      if (val) {
        this.is_mirror_active = false;
        this.flip();
      } else {
        this.deactivate_all();
      }
    },

    is_mirror_active(val) {
      if (val) {
        this.is_flip_active = false;
        this.mirror();
      } else {
        this.deactivate_all();
      }
    }
  }
};
</script>
