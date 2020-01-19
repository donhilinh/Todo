<template>
  <div >
    <h1>Test2</h1>
    <ul>
      <li v-for="(data, index) in artists " :key="index">
        <h3>
          {{data.name}}
        </h3>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Test2',
  props: {
    artists: {
      type: Array
    }
  },
  data(){
      return{}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li{
    height: 40px;
    width: 100%;
    padding: 15px;
    border: 1px solid saddlebrown;
    display: flex;
    justify-content: center;
    align-items: center;
  }  
a {
  color: #42b983;
}
</style>
