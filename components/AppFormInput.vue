<template>
  <div class="form-element mr-2" :class="{error: error}">
    <label :for="id">{{label}}</label>
    <input
        type="text"
        :id="id"
        :placeholder="placeholder"
        :value="modelValue"
        @input="onChange">
    <small v-if="error">{{error}}</small>
  </div>
</template>

<script>
export default {
  name: "AppFormInput",
  emits: ['update:modelValue'],
  props: {
    modelValue: String,
    error: String,
    label: String,
    placeholder: String
  },
  data () {
    return {
      id: 'form-el-' + Math.random()
    }
  },
  methods: {
    onChange(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>
