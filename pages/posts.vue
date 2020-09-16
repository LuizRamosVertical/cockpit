<template>
  <v-container >
    <!-- <v-btn
      color="blue-grey"
      class="ma-2 white--text"
      @click="acionar"
    >
      Upload
      <v-icon right dark>mdi-cloud-upload</v-icon>
    </v-btn> -->
    <v-row>
      <v-col cols="12">
        <v-data-table
          :headers="headers"
          :items="posts"
          class="elevation-1"
        >
          <template v-slot:top>
            <v-toolbar flat dark color="primary">
              <v-toolbar-title>Meus Posts</v-toolbar-title>
            </v-toolbar>
            <v-divider class="mx-4" inset vertical />
            <v-spacer />
            <v-dialog v-model="dialog" max-width="500px">
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  color="primary"
                  dark
                  class="mb-2"
                  v-bind="attrs"
                  v-on="on">
                  Criar
                </v-btn>
              </template>
              <v-card>
                <v-card-title>
                  <span class="headline">{{ formTitle }}</span>
                </v-card-title>

                <v-card-text>
                  <v-container>
                    <v-row>
                      <v-col cols="12" sm="12" md="12">
                        <v-text-field v-model="editedItem.id" label="ID" />
                      </v-col>

                      <v-col cols="12" sm="12" md="12">
                        <v-text-field v-model="editedItem.title" label="Título" />
                      </v-col>

                      <v-col cols="12" sm="12" md="12">
                        <v-textarea
                          v-model="editedItem.body"
                          label="body"
                        />
                        <!-- <v-text-field v-model="editedItem.body" label="body" /> -->
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>

                <v-card-actions>
                  <v-spacer />
                  <v-btn color="blue darken-1" text @click="close">Cancelar</v-btn>
                  <v-btn color="blue darken-1" text @click="save">Salvar</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </template>
          <template v-slot:item.actions="{ item }">
            <v-icon
              small
              class="mr-2"
              @click="editItem(item)"
            >
              mdi-pencil
            </v-icon>
            <v-icon
              small
              @click="deleteItem(item)"
            >
              mdi-delete
            </v-icon>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>
 <!--
<script src="http://localhost:5005/socket.io/socket.io.js"></script>
-->
<script>
export default {
  name: 'Posts',
  data () {
    return {
      dialog: false,
      headers: [
        {
          text: 'ID',
          value: 'id'
        },
        {
          text: 'Título',
          value: 'title'
        },
        {
          text: 'Corpo',
          value: 'body',
          sortable: false
        },
        {
          text: 'Ações',
          value: 'actions',
          sortable: false
        }
      ],
      posts: [],
      editedIndex: -1,
      editedItem: {
        id: 0,
        title: '',
        body: ''
      },
      defaultItem: {
        id: 0,
        title: '',
        body: ''
      }
    }
  },
  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'Novo Post' : 'Alterar Post'
    }
  },
  watch: {
    dialog (val) {
      val || this.close()
    }
  },
  // async mounted () {

  //   try {
  //     this.socket = this.$nuxtSocket({ })
  //     /* Listen for events: */

  //     console.log(this.socket);
  //     await this.socket.on('connect', (msg, cb) => {
  //       window.console.log('emitir')
  //       this.socket.emit('authenticate', {
  //         token:
  //           '3Jk3BJ]Ou8kj9RT7Kelri5F7tBJXZ7EWYJpqkuMNfxb2XDOtrxHqtZVXbtgnruWGsjxiZvcUhecWUqIp078HlJegPNacs1yqSeaS9nrHaxnKOV5BBtSXbCxnaSU84Ujt4HWklAh3SjCbkPndHiTsX5NTUgnrUTCObVTzUZ8mNFFvo7Aht59HG3slDwpA4QQAApxSKzbdIGVZ3W6XZ7qIu3TmWQ2EpVaY6oL1Gsb83MRShmOgkE5VPebO2i1PPMbtjX7ADT'
  //       })
  //     })
  //   } catch (e) {
  //     window.console.log(e)
  //   }
  // },
  created () {
    this.initialize()
  },
  methods: {
    // async acionar () {
    //   window.console.log('antes')
    //   try {
    //     const identifyUser = 1
    //     window.console.log(identifyUser)
    //     window.console.log(this.socket);
    //     await this.socket.emit('CreateUser', identifyUser  , (user) => {
    //       window.console.log(user)
    //     })
    //   } catch (e) {
    //     window.console.log(e)
    //   }
    // }
    initialize () {
      this.posts = [
        {
          id: 1,
          title: 'Post 1',
          body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
        },
        {
          id: 2,
          title: 'Post 2',
          body: '2Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
        },
        {
          id: 3,
          title: 'Post 3',
          body: '3Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
        },
        {
          id: 4,
          title: 'Post 4',
          body: '4Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'
        }
      ]
    },
    editItem (item) {
      this.editedIndex = this.posts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },
    deleteItem (item) {
      const index = this.posts.indexOf(item)
      confirm('Are you sure you want to delete this item?') && this.posts.splice(index, 1)
    },
    close () {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.posts[this.editedIndex], this.editedItem)
      } else {
        this.posts.push(this.editedItem)
      }
      this.close()
    }
  }
}
</script>

<style scoped>

</style>
