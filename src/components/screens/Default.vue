<template>
  <div class="vml-default">
    <div class="vml-container">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner">
          Our Speakers
        </span>
      </h1>
      <section class="vml-flex-row">
        <div class="vml-flex-item vml-speaker" v-for="speaker in speakers">
          <h2 class="vml-speaker__title">{{ speaker.name }}</h2>
          <img class="vml-speaker__image" :src="speaker.headshot" />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'default-view',
  methods: {
  },
  data() {
    return {
      speakers: [
        {
          name: 'Bill Dinger',
          headshot: '/static/dinger.jpg',
        },
        {
          name: 'Heather Downing',
          headshot: '/static/downing.jpg',
        },
        {
          name: 'David Mitchell',
          headshot: '/static/mitchell.jpg',
        },
        {
          name: 'Jerome Scheuring',
          headshot: '/static/scheuring.jpg',
        },
      ],
    };
  },
};
</script>
