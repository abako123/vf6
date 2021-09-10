<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <site-title :title="title"></site-title>
      <v-spacer/>
      <v-btn icon @click="save"><v-icon>mdi-check</v-icon></v-btn>
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer">
      <site-menu></site-menu>
    </v-navigation-drawer>

    <v-content>
      <router-view/>
    </v-content>

    <site-footer :footer="footer"></site-footer>
  </v-app>
</template>

<script>
import SiteTitle from '@/components/site/title'
import SiteMenu from '@/components/site/menu'
import SiteFooter from '@/components/site/footer'

export default {
  components: { SiteTitle, SiteFooter, SiteMenu },
  name: 'App',
  data () {
    return {
      drawer: false,
      items: [],
      title: 'Welcome to ABAKO',
      footer: 'ABAKO-Simsan'
    }
  },
  mounted () {
    console.log(this.$firebase)
  },
  methods: {
    save () {
      console.log('save@@@')
      this.$firebase.database().ref().child('abcd').child('abcd').child('abcd').set({
        title: 'abcd', text: 'tttttt'
      })
    }
  }
}
</script>
