<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
    ></v-data-table>

    <v-snackbar v-model="snackbar">
      {{ currentItem }}
      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false"> Close </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import employeesList from '@/data/employees.json'

export default {
  data() {
    return {
      currentItem: '',
      snackbar: false,
      employees: employeesList,
      headers: [
        {
          text: 'Employee ID',
          value: 'id',
        },
        { text: 'Name', value: 'name' },
        { text: 'Psotion title', value: 'title' },
        { text: 'Salary ($)', value: 'salary' },
      ],
    }
  },
  methods: {
    selectRow(event) {
      this.snackbar = true
      this.currentItem = `${event.name}: ${event.title}`
    },
  },
}
</script>

<style scoped></style>
