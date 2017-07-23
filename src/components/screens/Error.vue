<template>
  <div class="vml-error">
    <div class="vml-container vml-container--sm">
      <h1>{{ message }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'error-view',
  props: ['message'],
};
</script>
