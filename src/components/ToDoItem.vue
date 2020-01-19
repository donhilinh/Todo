<template>
  <div class="todo_item">
    <b-list-group>
      <b-list-group-item
        class="d-flex justify-content-between"
        v-for="(data, index) in $attrs.list_data_Todo"
        :key="index"
        v-bind:style="{background:$attrs.color}"
        
      >
        <b-form-checkbox
          id="checkbox-1"
          name="checkbox-1"
          v-model="status"
          value="accepted"
          unchecked-value="not_accepted"
        >{{data.content}}</b-form-checkbox>
        <b-icon-x v-on:click="$emit('remove', index)"></b-icon-x>
      </b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  data() {
    console.log(this);
    return {
      status: []
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
