<template>
  <div>
    <table>
      <tr>
        <th v-for="th in head" :key="th">{{th}}</th>
      </tr>
      <slot></slot>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    head:Array
  },
  name: 'TableWrapper'
}
</script>

<style scoped>
table, th, td {
  border: 1px solid rgb(215, 215, 215);
  border-collapse: collapse;
}
table tr th{
  text-align: left;
  padding: 0 10px;
}
table tr{
  padding: 10px 10px!important;
  border: 1px solid rgb(215, 215, 215);
  border-collapse: collapse;
}
table{
  width: 70%!important;
  margin: 0 auto;
}
</style>
