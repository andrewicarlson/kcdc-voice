<template>
  <div class="vml-grid">
    <div class="vml-container vml-container--wide">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner">#&nbsp;&nbsp;{{ title }}</span>
      </h1>
      <section class="vml-grid-row">
        <div class="vml-grid-item" v-for="item in items">
          <div class="vml-grid-item__content">
            <div class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.speaker }}</div>
            <div class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.location }}</div>
            <div class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.time }}</div>
            <h2 class="vml-grid-item__title">{{ item.title }}</h2>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'list-view',
  props: ['title', 'items'],
};
</script>
