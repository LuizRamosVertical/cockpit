<template>
  <div>
    <h1 class="display-2 text-right"></h1>
    <v-btn text small>Normal</v-btn>
    <v-btn icon color="primary">
      <v-icon>mdi-plus</v-icon>
    </v-btn>
    <v-overflow-btn
          class="my-2"
          :items="dropdown_font"
          label="Overflow Btn"
          target="#dropdown-example"
        ></v-overflow-btn>
    <v-btn
      color="blue-grey"
      class="ma-2 white--text"
      @click="acionar"
    >
      Upload
      <v-icon right dark>mdi-cloud-upload</v-icon>
    </v-btn>
  </div>
</template>

<script>

export default {
  data: () => ({
    dropdown_font: ['Arial', 'Calibri', 'Courier', 'Verdana'],
    dropdown_icon: [
      { text: 'list', callback: () => console.log('list') },
      { text: 'favorite', callback: () => console.log('favorite') },
      { text: 'delete', callback: () => console.log('delete') }
    ],
    dropdown_edit: [
      { text: '100%' },
      { text: '75%' },
      { text: '50%' },
      { text: '25%' },
      { text: '0%' }
    ]
  }),
  // async mounted () {
  //   try {
  // this.socket = this.$nuxtSocket({ })
  // /* Listen for events: */

  // window.console.log(this.socket)
  // await this.socket.on('connect', (msg, cb) => {
  //   window.console.log('emitir')
  //   this.socket.emit('authenticate', {
  //     token:
  //       '3Jk3BJ]Ou8kj9RT7Kelri5F7tBJXZ7EWYJpqkuMNfxb2XDOtrxHqtZVXbtgnruWGsjxiZvcUhecWUqIp078HlJegPNacs1yqSeaS9nrHaxnKOV5BBtSXbCxnaSU84Ujt4HWklAh3SjCbkPndHiTsX5NTUgnrUTCObVTzUZ8mNFFvo7Aht59HG3slDwpA4QQAApxSKzbdIGVZ3W6XZ7qIu3TmWQ2EpVaY6oL1Gsb83MRShmOgkE5VPebO2i1PPMbtjX7ADT'
  //   })
  // })
  //   } catch (e) {
  //     window.console.log(e)
  //   }
  // },
  methods: {
    acionar  () {
    }
  }
}
</script>
