<template>
  <v-container>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      color="white"
      :permanent="permanent"
      app
      >
      <v-list
        dense
        nav
        class="py-0"
      >
          <v-list-item two-line :class="miniVariant && 'px-0'">
          <v-list-item-logo>
            <img height="57px" v-if="miniVariant" src="https://i.ibb.co/NtD41h6/Vertical-Logo.png">
            <img v-else src="https://vertical.fluigidentity.com/cloudpass/assets/image/company/small/55b7fc0ed33c11e9934b0a5864604397.png">
          </v-list-item-logo>
        </v-list-item>

         <v-divider/>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
              <v-menu open-on-hover top offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                light
                color="grey"
                dark
                v-bind="attrs"
                v-on="on"
                icon
                left
              >Hover
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                v-for="(item, index) in items"
                :key="index"
                @click="abrirFecharMenu"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      color="??F0F8FF"
      app
      dark
    >
    <v-app-bar-nav-icon @click="abrirFecharMenu" />

      <v-toolbar-title></v-toolbar-title>

      <v-spacer />

      <v-btn icon>
        <v-icon>mdi-account</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-container>
</template>

<script>
export default {
  name: 'MainNav',
  data () {
    return {
      drawer: null,
      clipped: true,
      fixed: false,
      miniVariant: false,
      permanent: true,
      items: [
        { title: 'Dashboard', icon: 'mdi-view-dashboard', to: '/' },
        { title: 'Banco de Horas', icon: 'mdi-post', to: '/banco_Horas' }
      ],
      right: null
    }
  },
  created () {
    this.handleResize()
  },
  mounted () {
    window.addEventListener('resize', this.handleResize)
  },
  methods: {
    handleResize () {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': {
          this.permanent = false
          break
        }
        case 'sm': {
          this.permanent = true
          break
        }
        case 'md': {
          this.permanent = true
          break
        }
        case 'lg': {
          this.permanent = true
          break
        }
        case 'xl': {
          this.permanent = true
          break
        }
      }
    },
    abrirFecharMenu () {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs': {
          this.miniVariant = false
          this.drawer = !this.drawer
          break
        }
        case 'sm': {
          this.miniVariant = !this.miniVariant
          this.drawer = !this.drawer
          break
        }
        case 'md': {
          this.miniVariant = !this.miniVariant
          this.drawer = !this.drawer
          break
        }
        case 'lg': {
          this.drawer = null
          this.miniVariant = !this.miniVariant
          break
        }
        case 'xl': {
          this.drawer = null
          this.miniVariant = !this.miniVariant
          break
        }
      }
    }
  }
}
</script>

<style scoped></style>
