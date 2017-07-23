<template>
  <div class="vml-list">
    <div class="vml-container">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner"> {{ title }}</span>
      </h1>
      <section class="vml-list-row">
        <div class="vml-list-item" v-for="item in items">
          <div class="vml-list-item__author-image" :style="{ backgroundImage: 'url(' + item.thumbnail + ')' }"></div>
          <div class="vml-list-item__content">
            <div v-if="item.time || item.speaker" class="vml-list-item__meta">{{ item.speaker }} | {{ item.time }} | {{ item.location }}</div>
            <h2 class="vml-list-item__title">{{ item.title }}</h2>
            <div class="vml-list-item__description">{{ item.description }}</div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'single-view',
  props: ['title', 'items'],
};
</script>
