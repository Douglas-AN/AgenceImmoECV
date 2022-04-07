<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input
      :id="id"
      :type="type"
      :name="name"
      :required="required"
      :value="value"
      @input="$emit('input', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  props: {
    id: String,
    type: String,
    name: String,
    label: String,
    required: Boolean,
    mailValue: String,
    value:[String, Number, Boolean],
  },
};
</script>
