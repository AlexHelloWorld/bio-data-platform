<template>
  <table>
    <tr>
      <th v-for="(head, key) in headers">
        <!-- do sort when click -->
        <span v-if="head.name && head.sortable" :id="key" @click="sort($event)" class="sortable-column">
              {{head.name}} <i :class="'fa ' + sortState[key]"></i>
            </span>
        <span v-else-if="head.name">
          {{head.name}}
        </span>
        <span v-else>
          {{head}}
        </span>
      </th>
    </tr>

    <tr id="data" v-for="patient in showData">
      <td v-for="(item, key) in patient">
          <span v-if="headers[key].leadTo">
            <router-link class="link-item" :to="'/'+headers[key].leadTo+'/'+item">{{item}}</router-link>
          </span>
        <span v-else>
            {{item}}
          </span>
      </td>
    </tr>
  </table>
</template>

<script>
  export default {
    name: 'TableItems',
    props: ['showData', 'headers', 'sortState', 'sortOrder', 'sort']
  }
</script>

<style scoped>
  table, td {
    border: 1px solid #999;
  }

  table {
    width: 100%;
    border-collapse: collapse;
  }

  th {
    text-align: left;
    padding: 0 8px;
    height: 40px;
    white-space: nowrap;
  }

  td {
    height: 40px;
    padding: 0 6px;
  }

  #data:hover {
    background-color: #666 !important;
    color: white;
  }

  #data:nth-child(even) {
    background-color: #f2f2f2
  }

  .sortable-column {
    cursor: pointer;
  }

  .link-item {
    text-decoration: none;
    color: inherit;
    border-bottom: dotted deepskyblue 2px;
  }

  .link-item {
    text-decoration: none;
    color: inherit;
    border-bottom: dotted deepskyblue 2px;
  }

</style>
