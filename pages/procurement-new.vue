<template>
<div class="login-page">

  <h1>New IRF</h1>


<!--the whole container-->
<v-layout flex align-center justify-center>
<v-flex xs10 sm10 elevation-6>
<v-card>
          
  <v-card-text class="pt-4">
  <div>
  <v-form ref="form">

    <!--first line-->
    <v-row>
      <v-col md="4">
      <v-text-field
        label="Name"
        outlined
        dense
        readonly
        :value="$auth.user.email"
      ></v-text-field>
      </v-col>

      <v-col md="4">
      <v-select
        :items="dept"
        label="Department"
        outlined
        dense
        required
        :rules="rules"
        hide-details="auto"
      ></v-select>
      </v-col>

      <v-col md="4">
      <v-text-field
        label="IRF no."
        outlined
        dense
        required
        disabled
      ></v-text-field>
      </v-col>

    </v-row>

    <!--second line-->
    <v-row>

      <v-col md="4">
      <v-text-field
        label="Date"
        outlined
        dense
        required
        :value="now"
        append-icon="mdi-calendar"
      ></v-text-field>
      </v-col>

      <!--date picker-->
      <v-col md="4">
      <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        :return-value.sync="date"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >

        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="date"
            label="Deadline"
            placeholder="Only when appliable"
            append-icon="mdi-calendar"
            outlined
            dense
            readonly
            v-bind="attrs"
            v-on="on"
          ></v-text-field>
        </template>

        <v-date-picker
          v-model="date"
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn text color="primary" @click="menu = false">
            Cancel
          </v-btn>
          <v-btn text color="primary" @click="$refs.menu.save(date)">
             OK
          </v-btn>
        </v-date-picker>
      </v-menu>
      </v-col>

      <v-col md="4">
      <v-text-field
        label="Project Code"
        outlined
        dense
        placeholder="Only when BDD"
      ></v-text-field>
      </v-col>
    </v-row>

    <!--third line-->
    <v-row>
      <v-col md="8">
        <v-text-field
        label="Title"
        outlined
        dense
        required
      ></v-text-field>
      </v-col>

      <v-col md="4">
      <v-select
        :items="purchaseCategory"
        label="Purchase Category"
        outlined
        dense
        required
      ></v-select>
      </v-col>
    </v-row>

    <!--fourth line-->
    <v-row>
      <v-col md="8">
        <v-textarea
          label="Item Description"
          outlined
          dense
          required
          hint="(Please state specification or model. Please attach any relevant documents for license certificate or any renewal etc.)"
          persistent-hint
      ></v-textarea>
      </v-col>

      <v-col md="4">
      <v-text-field
        label="Quantity"
        outlined
        dense
      ></v-text-field>
      </v-col>
    </v-row>


    <v-layout justify-space-between>
      <v-btn>Submit</v-btn>
    </v-layout>

  </v-form>
  </div>
  </v-card-text>
</v-card>
</v-flex>
</v-layout>
</div>
</template>

<script>
export default {
  data: () => ({
    rules: [ value => !!value || 'Required.' ],
    dept: [ 'Accounts & Finance Department', 'BOD', 'Business Development Department', 'CEO\'s Office', 'Chairman\'s Office', 'COO\'s Office',
            'Corporate Services Unit', 'Customer Service', 'Data Centre', 'Digital Heritage', 'Director', 'HR & Administration', 'Information Security',
            'Infrastructure & Development', 'IT Security', 'Komunikasi Sri Bumi', 'KPSKTM', 'MD\'s Office', 'Network', 'Operation Department',
            'Procurement & Logistics Unit', 'Public Affairs Department', 'Quality Management Systems', 'Research & Innovation', 'Sales Department',
            'State Data Centre', 'Systems' ],
    now: new Date().toISOString().slice(0,10),
    purchaseCategory: ['Printing & Stationary', 'Insurance', 'Service & Maintenance', 'Staff Amentities', 'Corporate Uniform', 'Resell', 'Others'],
  }),
}
</script>
