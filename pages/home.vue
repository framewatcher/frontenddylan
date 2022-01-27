<template>
  

  <v-container>
  <v-row dense align="stretch">
  
    <v-col cols="8">
      <v-row dense align="stretch" >

          <v-col cols="9">
            <v-card height=250px>
              <v-card-text>
                <h2 class="text-truncate">Welcome Back John</h2>
                <blockquote>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer rhoncus metus id justo pretium interdum. Integer maximus neque id orci luctus, ac interdum nisi viverra.</blockquote>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="3">
            <v-card height="48%">
              <v-card-text>
                <h5 class="text-truncate text-uppercase" >Time</h5>
                <v-icon x-large>mdi-clock</v-icon>
              </v-card-text>
            </v-card>

            <v-card height="4%" />

            <v-card height="48%">
              <v-card-text>
                <h5 class="text-truncate text-uppercase">My Dept Availability</h5>
                <v-icon x-large>mdi-account-multiple</v-icon>
              </v-card-text>
            </v-card>
          </v-col>
      </v-row>


      <v-row dense align="stretch">
        <v-col cols="4">
          <v-card height=250px>
            <v-card-text>
              <h5 class="text-truncate text-uppercase">Leave</h5>
              <v-icon x-large>mdi-beach</v-icon>
            </v-card-text>
          </v-card>
        </v-col>

        <v-col cols="4">
          <v-card min-height="100%">
            <v-card-text>
              <h5 class="text-truncate text-uppercase">Medical</h5>
              <v-icon x-large>mdi-medical-bag</v-icon>
            </v-card-text>
          </v-card>
        </v-col>

        <v-col cols="4">
          <v-card min-height="100%">
            <v-card-text>
              <h5 class="text-truncate text-uppercase">Time Attendance</h5>
              <v-icon x-large>mdi-calendar-clock</v-icon>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-col>


    <v-col cols="4">
      <v-card min-height="100%">
        <v-card-text>
          <h5 class="text-truncate text-uppercase">Calendar</h5>
          <v-icon x-large>mdi-calendar</v-icon>
        </v-card-text>
      </v-card>
    </v-col>
    
  </v-row>
</v-container>
      
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>
