<template>
  <v-app dark>
    <v-navigation-drawer :mini-variant.sync="miniVariant" v-model="drawer" fixed app>
      <v-toolbar flat class="transparent">
        <v-list class="pa-0">
          <v-list-tile avatar>
            <v-list-tile-avatar>
              <img :src="profileImage">
            </v-list-tile-avatar>

            <v-list-tile-content>
              <v-list-tile-title>Sharon</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-toolbar>
      <v-list class="pt-0" dense>
        <v-divider></v-divider>
        <v-list-tile router :to="item.to" :key="i" v-for="(item, i) in items">
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar fixed app dark :clipped-left="clipped" color="indigo">
      <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'"></v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>web</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer temporary :right="right" v-model="rightDrawer" fixed>
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-footer :fixed="fixed" app dark color="indigo">
      <span>&copy; 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: null,
        fixed: false,
        items: [
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'bubble_chart', title: 'Posts', to: '/posts' },
          { icon: 'account_circle', title: 'Admin', to: '/admin' }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Nuxt blog',
        profileImage: 'https://scontent.fcok1-1.fna.fbcdn.net/v/t1.0-9/19113766_1097897530354278_8129712611027682718_n.jpg?_nc_cat=0&oh=c32dda46cb47c4091f08fc5252c2d00f&oe=5BC847D3'
      }
    }
  }
</script>
