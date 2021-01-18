<template>
  <canvas ref="canvas"/>
</template>

<script>
export default {
  name: 'Captcha',
  props: {
    phraseLength: {
      type: Number,
      default: 8
    },
    alphabet: {
      type: String,
      default: 'abcdefghijklmnopqrstuvwxyz0123456789+-*§$%&'
    },
    fontSize: {
      type: String,
      default: '16px'
    },
    fontFamily: {
      type: String,
      default: 'Verdana'
    },
    canvasSize: {
      type: Object,
      default: () => ({
        width: 100,
        height: 24
      })
    },
    canvasPosition: {
      type: Object,
      default: () => ({
        x: 0,
        y: 16
      })
    },
    userInputForPassphrase: {
      required: true
    }
  },
  mounted () {
    const canvas = this.$refs.canvas
    canvas.width = this.canvasSize.width
    canvas.height = this.canvasSize.height
    const ctx = canvas.getContext('2d')
    ctx.font = `${this.fontSize} ${this.fontFamily}`
    ctx.strokeText(
      this.passphrase,
      this.canvasPosition.x,
      this.canvasPosition.y
    )
  },
  methods: {
    getRandomCharFromAlphabet () {
      return this.alphabet[Math.floor(Math.random() * this.alphabet.length)]
    }
  },
  computed: {
    passphrase () {
      return Array.from(new Array(this.phraseLength), () => this.getRandomCharFromAlphabet()).join('')
    }
  },
  watch: {
    userInputForPassphrase (val) {
      this.$emit(`${val === this.passphrase ? 'right' : 'wrong'}-passphrase`)
    }
  }
}
</script>

<style scoped>

</style>
