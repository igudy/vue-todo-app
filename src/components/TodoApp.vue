<template>
  <div class="container">
    <h1 class="text-center" mt-5>Vue Todo List</h1>

    <!-- Input -->
    <div class="d-flex">
      <input type="text" class="form-control">
      <button class="btn btn-warning rounded-0">Submit</button>
    </div>
    <br>

    <!-- Task Table -->
    <table class="table table-hover table-dark">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col">#</th>
          <th scope="col">#</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Buy snacks for this evening</td>
          <td>pending</td>
          <td>@games</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Play Uncharted this night</td>
          <td>todo</td>
          <td>@fat</td>
        </tr>
      </tbody>
    </table>


  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    // msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
