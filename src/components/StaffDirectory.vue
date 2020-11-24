<template>
  <div class="ui container">
    <input v-model="filterBy" placeholder="Filter By Last Name">
    <table class="ui celled table">
      <thead>
      <tr>
        <th>Avatar</th>
        <th @click="sortBy = 'firstName'">First Name</th>
        <th @click="sortBy = 'lastName'">Last Name</th>
        <th @click="sortBy = 'email'">Email</th>
        <th @click="sortBy = 'phone'">Phone</th>
        <th @click="sortBy = 'department'">Department</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(employee, index) in sortedEmployees" :key="index">
        <td>
          <img :src="employee.photoUrl" class="ui mini rounded image"/>
        </td>
        <td>{{ employee.firstName }}</td>
        <td>{{ employee.lastName }}</td>
        <td>{{ employee.email }}</td>
        <td>{{ employee.phone }}</td>
        <td>{{ employee.department }}</td>
      </tr>
      </tbody>
      <tfoot>
      <tr>
        <th colspan="6">{{ sortedEmployees.length }} employees</th>
      </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
export default {
  name: 'StaffDirectory',
  data() {
    return {
      employees: [
        {
          firstName: 'amelia',
          lastName: 'austin',
          photoUrl: 'https://randomuser.me/api/portraits/thumb/women/9.jpg',
          email: 'amelia.austin@example.com',
          phone: '(651)-507-3705',
          department: 'Engineering',
        },
        {
          firstName: 'bobbie',
          lastName: 'murphy',
          photoUrl: 'https://randomuser.me/api/portraits/thumb/women/79.jpg',
          email: 'bobbie.murphy@example.com',
          phone: '(925)-667-7604',
          department: 'Management',
        },
        {
          firstName: 'kristin',
          lastName: 'terry',
          photoUrl: 'https://randomuser.me/api/portraits/thumb/women/45.jpg',
          email: 'kristin.terry@example.com',
          phone: '(021)-544-1184',
          department: 'Sales',
        },
        {
          firstName: 'brandon',
          lastName: 'griffin',
          photoUrl: 'https://randomuser.me/api/portraits/thumb/men/59.jpg',
          email: 'brandon.griffin@example.com',
          phone: '(509)-317-9506',
          department: 'Management',
        },
        {
          firstName: 'tammy',
          lastName: 'gibson',
          photoUrl: 'https://randomuser.me/api/portraits/thumb/women/72.jpg',
          email: 'tammy.gibson@example.com',
          phone: '(815)-727-0663',
          department: 'Support',
        },
      ],
      sortBy: 'firstName',
      filterBy: '',
    };
  },
  computed: {
    sortedEmployees() {
      return this.employees.filter(
        employee => employee.lastName.includes(this.filterBy),
      )
        .sort(
          (a, b) => a[this.sortBy].localeCompare(b[this.sortBy]),
        );
    },
  },
};
</script>

<style scoped>
h1.ui.center.header {
  margin-top: 3em;
}

.ui.table th:not(:first-child):hover {
  cursor: pointer;
}

input {
  padding: 3px;
}
</style>
