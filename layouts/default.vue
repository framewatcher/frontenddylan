<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="clipped"
      expand-on-hover
      permanent
      fixed
      app
    >
      <v-list>
        <v-list-group
          v-for="item in items"
          :key="item.title"
          v-model="item.active"
          :prepend-icon="item.icon"
          no-action
          dense
        >
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title v-text="item.title"></v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item
            v-for="child in item.items"
            :key="child.title"
            :to="child.to"
            router
            dense
          >
            <v-list-item-content>
              <v-list-item-title v-text="child.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>


    <v-app-bar :clipped-left="clipped" fixed app>

      <v-spacer />

      <v-text-field />

      <v-btn icon class="search">
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon class="notification">
        <v-icon>mdi-bell</v-icon>
      </v-btn>


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
    </v-app-bar>
    

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data:() => ({
    items: [
      {
        title: 'Welcome',
        icon: 'mdi-home',
        items: [{ title: 'Home', to: '/home' }],
      },
      {
        title: 'E-Leave',
        icon: 'mdi-beach',
        items: [
          { title: 'My Application',      to: '/leave-balance' },
          { title: 'E-Leave Application', to: '/leave-apply'   },
          { title: 'Who is on leave?',    to: '/leave-who'     }
        ],
      },
      {
        title: 'Time Attendance',
        icon: 'mdi-calendar-range',
        items: [{ title: 'View Attendance', to: '/attendance' }],
      },
      {
        title: 'Reservation',
        icon: 'mdi-car-select',
        items: [
          { title: 'View My Reservations', to: '/reserve-view' },
          { title: 'Search Reservations',  to: '/reserve-search' },
          { title: 'Make Reservation',     to: '/reserve-make' }
        ],
      },
      {
        title: 'Serial Numbering',
        icon: 'mdi-clipboard-list-outline',
        items: [
          { title: 'Generate Serial Number', to: '/number-generate' },
          { title: 'Serial Number Record',   to: '/number-record' },
          { title: 'Client Code',            to: '/number-client' },
          { title: 'Add Client',             to: '/number-add' }
        ],
      },
      {
        title: 'Staff Training',
        icon: 'mdi-account-tie',
        items: [{ title: 'View My Training Records', to: '/training' }],
      },
      {
        title: 'Medical',
        icon: 'mdi-medical-bag',
        items: [
          { title: 'My Medical Balances',      to: '/medical-balance' },
          { title: 'View Panel Clinic Visits', to: '/medical-view-panel' },
          { title: 'Add Panel Clinicl Visit',  to: '/medical-add-panel' },
          { title: 'View Medical Activities',  to: '/medical-activity' }
        ],
      },
      {
        title: 'Procurement',
        icon: 'mdi-cart-arrow-down',
        items: [
          { title: 'New Initial Request Form',  to: '/procurement-new' },
          { title: 'View Initial Request Form', to: '/procurement-view' }
        ],
      },
      {
        title: 'Event',
        icon: 'mdi-calendar',
        items: [{ title: 'Sabah Net Events', to: '/event' }],
      },
      {
        title: 'Asset Movement',
        icon: 'mdi-archive sync-outline',
        items: [
          { title: 'View My Asset Movement',      to: '/asset' },
          { title: 'View My Dept Asset Movement', to: '/asset-dept' },
          { title: 'Add Asset Movement',          to: '/asset-add' },
          { title: 'Accept Asset Movement',       to: '/asst-accept' }
        ],
      },
      {
        title: 'Availability',
        icon: 'mdi-account-multiple-check-outline',
        items: [{ title: 'View Availability', to: '/availability' }],
      },
    ],
  }),
}
</script>
