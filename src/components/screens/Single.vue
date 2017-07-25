<template>
  <div class="vml-grid">
    <div class="vml-container">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner">#&nbsp;&nbsp;{{ title }}</span>
      </h1>
      <section class="vml-speaker-row" v-if="speaker">
        <div class="vml-grid-item">
          <div class="vml-grid-item__author-image" :style="{ backgroundImage: 'url(' + speaker.thumbnail + ')' }"></div>
          <div class="vml-grid-item__content">
            <h2 class="vml-grid-item__title">{{ speaker.title }}</h2>
            <div class="vml-grid-item__description">{{ speaker.description }}</div>
          </div>
        </div>
      </section>
      <section class="vml-grid-row">
        <div class="vml-grid-item" v-for="item in items">
          <div v-if="!speaker" class="vml-grid-item__author-image" :style="{ backgroundImage: 'url(' + item.thumbnail + ')' }"></div>
          <div class="vml-grid-item__content">
            <div v-if="!speaker" class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.speaker }}</div>
            <div class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.location }}</div>
            <div class="vml-grid-item__meta">//&nbsp;&nbsp;{{ item.time }}</div>
            <h2 class="vml-grid-item__title">{{ item.title }}</h2>
            <div class="vml-grid-item__description">{{ item.description }}</div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'single-view',
  props: ['title', 'items', 'speaker'],
};
</script>
