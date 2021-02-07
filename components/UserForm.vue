<template>
  <section>
    <card>
      <b-field label="Name" horizontal>
        <b-input
          v-model="newName"
          expanded
          rounded
          placeholder="Enter your name"
        ></b-input>
      </b-field>
      <b-field label="Email" horizontal>
        <b-input
          v-model="newEmail"
          expanded
          rounded
          placeholder="Enter your email"
        ></b-input>
      </b-field>
      <b-field label="Age" horizontal>
        <b-input
          v-model="newAge"
          expanded
          rounded
          placeholder="Enter your age"
        ></b-input>
      </b-field>

      <b-button
        class="mt-10"
        type="is-primary"
        rounded
        expanded
        @click="saveUser"
      >
        Save user
      </b-button>
    </card>
  </section>
</template>

<script>
import Card from '@/components/Card'
export default {
  components: {
    Card,
  },
  props: {
    name: { type: String, default: null },
    email: { type: String, default: null },
    age: { type: Number, default: null },
  },
  data() {
    return {
      newName: null,
      newEmail: null,
      newAge: null,
    }
  },
  mounted() {
    this.newName = this.name
    this.newAge = this.age
    this.newEmail = this.email
  },
  methods: {
    saveUser() {},
  },
}
</script>
