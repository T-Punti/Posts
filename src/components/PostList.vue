<template>
  <div>
    <div v-if="error">
      <h2>{{ error }}</h2>
    </div>
    <div v-else>
      <div v-if="loading">
        <h2>Loading DATA ...</h2>
      </div>
    </div>
    <h1>POSTS</h1>
    <table>
      <thead>
        <tr>
          <th>UserID</th>
          <th>Index</th>
          <th>Title</th>
          <th>Body</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data">
          <td>{{ item.userId }}</td>
          <td>{{ item.id }}</td>
          <td>{{ item.title }}</td>
          <td>{{ item.body }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { useFetch } from '../composable/UseFetch.js';
const prev = 0;
export default {
  name: 'UserList',
  setup() {
    const { data, error, loading } = useFetch(
      'https://jsonplaceholder.typicode.com/posts',
      {}
    );
    return {
      data,
      error,
      loading,
      prev,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
