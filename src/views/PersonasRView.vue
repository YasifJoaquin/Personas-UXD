<template>
  <div class="p-4 grid grid-cols-3 sm:grid-cols-1">
    <h1 class="text-2xl font-bold mb-4">Dynamic Form</h1>
    <form>
      <div v-for="(field, index) in fields" :key="index">
        <label :for="field.name" >{{ field.label }}</label>
        <input :id="field.name" :name="field.name" v-model="field.value" :type="field.type" :placeholder="field.placeholder" class="border border-gray-400 p-2 rounded-lg w-full mb-4">
      </div>
    </form>
    <button @click="addField" class="bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600">Add Field</button>
  </div>
</template>

<script>
export default {
  name: 'DynamicForm',
  data() {
    return {
      fields: [
        { label: 'Name', name: 'name', type: 'text', placeholder: 'Enter your name', value: '' },
        { label: 'Email', name: 'email', type: 'email', placeholder: 'Enter your email', value: '' },
        { label: 'Password', name: 'password', type: 'password', placeholder: 'Enter your password', value: '' }
      ]
    }
  },
  methods: {
    addField() {
      this.fields.push({ label: 'New Field', name: '', type: 'text', placeholder: '', value: '' });
    }
  }
}
</script>
