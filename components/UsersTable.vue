<template>
  <section>
    <b-field grouped group-multiline>
      <b-button
        label="Add User"
        type="is-primary"
        icon-left="plus"
        class="field"
        rounded
        @click="openAddUserModal"
      />
      <b-button
        label="Delete checked"
        type="is-danger"
        icon-left="close"
        class="field"
        rounded
        @click="checkedRows = []"
      />
    </b-field>
    <b-table
      class="mt-6"
      hoverable
      striped
      focusable
      :data="data"
      bordered
      checkable
      :checked-rows.sync="checkedRows"
      paginated
      backend-pagination
      @click="editItem"
    >
      <template v-for="column in columns">
        <b-table-column :key="column.email" v-bind="column">
          <template v-if="column.searchable" #searchable="props">
            <b-input
              v-model="props.filters[props.column.field]"
              placeholder="Search..."
              icon="magnify"
              size="is-small"
              rounded
              expanded
            />
          </template>
          <template #default="props">
            {{ props.row[column.field] }}
          </template>
        </b-table-column>
      </template>

      <template #empty>
        <div class="columns">
          <div class="column has-text-centered">
            <b-button type="is-primary" rounded class="has-text-centered">
              No users yet, Add a new user
            </b-button>
          </div>
        </div>
      </template>
    </b-table>
  </section>
</template>

<script>
import UserForm from '@/components/UserForm'

export default {
  data() {
    return {
      data: [{ name: 'Julio', email: 'julio@lugo.com', age: 25 }],
      checkedRows: [],
      columns: [
        {
          field: 'name',
          label: 'Name',
        },
        {
          field: 'email',
          label: 'Email',
          searchable: true,
        },
        {
          field: 'age',
          label: 'Age',
          numeric: true,
        },
      ],
    }
  },
  mounted() {
    // fetch('http://localhost:8000/')
  },
  methods: {
    openAddUserModal() {
      const { $buefy } = this

      $buefy.modal.open({
        parent: this,
        component: UserForm,
        hasModalCard: true,
        trapFocus: true,
      })
    },
    editItem(item) {
      // eslint-disable-next-line
      const { $buefy } = this

      $buefy.modal.open({
        parent: this,
        component: UserForm,
        hasModalCard: true,
        trapFocus: true,
        props: {
          ...item,
        },
      })
    },
  },
}
</script>
