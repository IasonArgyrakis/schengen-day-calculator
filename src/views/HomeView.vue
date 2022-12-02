<template>
  <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col

      >
        <v-card

        >
          <v-card-title>
            How it works
          </v-card-title>
          <v-card-text>
            Start by Entering the dates of your trip below


          </v-card-text>
          <v-container class="grey lighten-5">
            <v-row>
              <v-col md="4">
                <v-date-picker
                    v-model="newDateRange"
                    range
                    full-width
                ></v-date-picker>
                <v-btn class="mt-4" elevation="2" color="primary"  block @click="save">Add Dates</v-btn>

              </v-col>
              <v-col md="8">
                <v-data-table
                    :headers="headers"
                    :items="daysInShengen"
                    class="elevation-1 mt-3 pt-2"
                >
                  <template v-slot:[`item.actions`]="{ item }">
                    <v-icon
                        small
                        @click="deleteItem(item)"
                    >
                      mdi-delete
                    </v-icon>
                  </template>
                  <template v-slot:no-data>
                    <p>No dates Added</p>
                  </template>
                </v-data-table>
              </v-col>
            </v-row>
          </v-container>


        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: 'HomeView',

  components: {},
  data() {
    return {

      editedItem: {
        start: undefined,
        end: undefined,
      },

      headers: [
        {
          text: 'Entry Date',
          align: 'start',
          sortable: true,
          value: 'startDate',
        },
        {
          text: 'Exit Date',
          sortable: false,
          value: 'endDate',
        },
        {
          text: '# of Days',
          sortable: false,
          value: 'count',
        },
        {
          text: 'Actions',
          sortable: false,
          value: 'actions',
        },

      ],
      newDateRange: [],
      daysInShengen: [],

    }
  },
  methods: {

    editItem(item) {
      this.editedIndex = this.days.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem(item) {
      this.daysInShengen.splice(item.index, 1)
    },


    save() {
      this.newDateRange.sort()
      this.daysInShengen.push(
          {
            startDate: new Date(this.newDateRange[0]),
            endDate: new Date(this.newDateRange[1]),
            count: ( new Date(this.newDateRange[1]).getTime()
                    - new Date(this.newDateRange[0]).getTime()
            ) / (1000 * 3600 * 24) } )
      this.newDateRange = []
      this.daysInShengen.sort();
      this.$forceUpdate()
    },
  }

}
</script>
