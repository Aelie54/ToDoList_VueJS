<template>
 <table class="table">
  <thead>
    <tr>
      <!-- <th scope="col">#</th> -->
      <th scope="col">Title</th>
      <th scope="col">Description</th>
      <th scope="col">Deadline</th>
      <th scope="col">Comment</th>
      <th scope="col">Make it? </th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="todo in getList" :key="todo">
      <!-- <th scope="row">1</th> -->
      <td>{{todo.title}}</td>
      <td>{{todo.description}}</td>
      <td>{{todo.deadline}}</td>
      <td>{{todo.comment}}</td>
      <td>delete</td>
    </tr>
  </tbody>
</table>
</template>

<script>
import { MyList } from "../stores/List";
import { mapState, mapWritableState } from "pinia";
export default {
computed: {
      ...mapState(MyList, ['getList'])
},
};
</script>
