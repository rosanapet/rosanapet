
<script>
  export default {
    name: 'Head',
    data: function () {
      return {
        title: 'ROSANA PET'
      }
    },
    // Usage with context the component
    head: {
      title: function () {
        return {
          // To use "this" in the component, it is necessary to return the object through a function
          inner: this.title,
          separator: ' ',
          complement: ' '
        }
      },
      meta: [
        { 'http-equiv': 'Content-Language', content: 'pt-br' }
      ],
      link: [
        { rel: "icon", type: "image/png", sizes:"16x16", href: require('../images/horse.png') }
      ]
    }
  }
</script>

<style scoped>

</style>

<!--//<meta http-equiv="Content-Language" content="pt-br">-->