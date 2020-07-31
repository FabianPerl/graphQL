<template>
  <pre class="borderCode">
  {{ content }}
  </pre>
</template>

<script>
export default {
  props: {
    content: {
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.borderCode {
  padding: 2px;
  border: 1px solid #888;
}
</style>
