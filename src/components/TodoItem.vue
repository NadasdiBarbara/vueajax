<template>
  <li>
      <div v-if="!edit">
        {{person}}
        <button @click="Edit">Edit</button>
      </div>
      <div v-if="edit">
          <input type="text" v-model="person">
          <button @click="Save">Save</button>
      </div>
  </li>
</template>

<script>
export default {
    props: ['todo'],
    data() {
        return {
            person: this.todo.person,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('todo-item-changed', {
                original: this.todo,
                new: {
                    person: this.person
                    },
            })
        }
    }
}
</script>

<style>

</style>