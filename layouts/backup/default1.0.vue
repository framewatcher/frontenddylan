<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
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
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn icon @click.stop="clipped = !clipped">
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn icon @click.stop="fixed = !fixed">
        <v-icon>mdi-minus</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <div class="authentication-buttons">
      <div v-if="$auth.loggedIn">
         {{ $auth.user.email }}
         <v-btn icon to="/logout" class="logout-btn">
            <v-icon light @click="$auth.logout()">mdi-logout</v-icon>
         </v-btn>
      </div>
      <div v-else>
         <v-btn icon to="/login" class="login-btn">
            <v-icon>mdi-login</v-icon>
         </v-btn>
         <v-btn icon to="/register" class="register-btn">
            <v-icon>mdi-account-key-outline</v-icon>
         </v-btn>
      </div>
      </div>
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-calendar-clock',
          title: 'E-Leave',
          to: '/leave',
        },
        {
          icon: 'mdi-calendar-range',
          title: 'Time Attendance',
          to: '/attendance',
        },
        {
          icon: 'mdi-car-select',
          title: 'Reservation',
          to: '/reservation',
        },
        {
          icon: 'mdi-clipboard-list-outline',
          title: 'Serial Numbering',
          to: '/numbering',
        },
        {
          icon: 'mdi-account-tie',
          title: 'Staff Training',
          to: '/training',
        },{
          icon: 'mdi-medical-bag',
          title: 'Medical',
          to: '/medical',
        },
        {
          icon: 'mdi-cart-arrow-down',
          title: 'Procurement',
          to: '/procurement',
        },
        {
          icon: 'mdi-calendar',
          title: 'Event',
          to: '/event',
        },{
          icon: 'mdi-archive sync-outline',
          title: 'Asset Movement',
          to: '/asset',
        },
        {
          icon: 'mdi-account-multiple-check-outline',
          title: 'Availability',
          to: '/availability',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js',
    }
  },
}
</script>
