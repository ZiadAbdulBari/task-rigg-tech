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

<style>
table, th, td {
  border: 1px solid rgb(215, 215, 215);
  border-collapse: collapse;
  padding: 5px 10px;
}
table tr th{
  text-align: left;
  font-weight: 700;
}
table tr{
  border: 1px solid rgb(215, 215, 215)!important;
}
table{
  width: 70%!important;
  margin: 0 auto;
}
</style>
