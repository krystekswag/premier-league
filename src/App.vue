<template>
  <div id="content">
    <Table />
    <Caption />
  </div>
</template>

<script>
import Table from './components/Table.vue';
import Caption from './components/Caption.vue';

export default {
  name: 'App',
  components: {
    Table,
    Caption,
  },
};
</script>

<style lang="scss">
  *, body{
    margin: 0;
    background-color: #E8F0F2;
    font-family: 'Heebo', sans-serif;
  }
  #content {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  @media (max-width: 480px){
    #content{
      height: 90vh;
      margin: 10px;
    }
  }
</style>
