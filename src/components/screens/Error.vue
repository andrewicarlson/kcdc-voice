<template>
  <div>
    <div class="vml-container vml-container--sm">
      <h1 class="vml-error">{{ message }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'error-view',
  props: ['message'],
};
</script>
