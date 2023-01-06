<template>
  <div class="app">
    <form class="app__form" @submit.prevent="addResolution">
      <label>
        <h1>New Year's Resolution Creator!</h1>
        <p>Add your resolutions here:</p>
        <input v-model="newResolution" />
      </label>
      <button type="submit">Add Resolution</button>
    </form>
    <table class="app__resolutions">
      <thead>
        <tr>
          <th>Resolution</th>
          <th>Completed</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="resolution in resolutions" :key="resolution">
          <td>{{ resolution.text }}</td>
          <td>
            <input type="checkbox" v-model="resolution.completed" />
          </td>
        </tr>
      </tbody>
    </table>
    <button class="button--print" @click="printPage">Print</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newResolution: '',
      resolutions: [],
    };
  },
  methods: {
    addResolution() {
      this.resolutions.push({ text: this.newResolution, completed: false });
      this.newResolution = '';
    },
    printPage() {
      window.print();
    },
  },
};
</script>
