<template>
  <td v-if="type == 'data'">
    {{ value }}
  </td>
  <td v-if="type == 'action'">
    <button @click="$emit('deleteRow', value)">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        width="18"
        height="18"
        fill="rgba(255,0,0,1)"
      >
        <path
          d="M4 8H20V21C20 21.5523 19.5523 22 19 22H5C4.44772 22 4 21.5523 4 21V8ZM6 10V20H18V10H6ZM9 12H11V18H9V12ZM13 12H15V18H13V12ZM7 5V3C7 2.44772 7.44772 2 8 2H16C16.5523 2 17 2.44772 17 3V5H22V7H2V5H7ZM9 4V5H15V4H9Z"
        ></path>
      </svg>
    </button>
  </td>
</template>

<script>
export default {
  props: {
    type: String,
    value: String
  },
   emits: ["deleteRow"],
  name: 'TableData',
}
</script>

<style scoped>
  button{
    border:1px solid rgb(195, 195, 195);
    border-radius: 5px;
    background-color: rgb(247, 247, 247);
    padding: 5px 10px;
  }
</style>
