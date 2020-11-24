<template>
  <div id="app">
    <h1 class="ui center aligned header">Staff Directory</h1>
    <StaffDirectory/>
  </div>
</template>

<script>
import 'semantic-ui-css/semantic.css';
import StaffDirectory from './components/StaffDirectory';

export default {
  name: 'App',
  components: {
    StaffDirectory,
  },
};
</script>
