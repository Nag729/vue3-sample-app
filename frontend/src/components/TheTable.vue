<template>
  <!-- table -->
  <div class="the-table table is-striped is-hoverable">
    <thead>
      <tr>
        <th>ID</th>
        <th>TITLE</th>
      </tr>
    </thead>
    <tbody>
      <template v-for="item in tableItems" :key="item.no">
        <tr>
          <td>{{ item.id }}</td>
          <td class="max-width">
            <a :href="item.url" target="_blank">{{ item.title }}</a>
          </td>
        </tr>
      </template>
    </tbody>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, reactive } from 'vue';

// types
interface TableItems {
  id: string
  title: string,
  url: string
}

export default defineComponent({
  name: 'TheTable',

  props: {
    // table data props
    tableItems: {
      type: Object as PropType<TableItems>,
      default: () => {
        return [
          {
            id: 1,
            title: 'Article one',
            url: ''
          },
          {
            id: 2,
            title: 'Article two',
            url: ''
          }
        ]
      }
    }
  },
});
</script>

<style scoped lang="scss">
.the-table {
  width: 80%;
  margin: 0 auto;
  text-align: center;
}

.max-width {
  width: 100%;
}
</style>
