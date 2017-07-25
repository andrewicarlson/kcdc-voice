<template>
  <div class="vml-default">
    <div class="vml-container">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner">#&nbsp;&nbsp;Our Speakers</span>
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
          headshot: 'https://lh6.googleusercontent.com/LLQh7OP5tGS0eot0em6u0bud9g7WrzmIF-0rWVLehuomaP-udQQZBtCsiKWlutBOMWNwYAiE=w2880-h1598',
        },
        {
          name: 'Heather Downing',
          headshot: 'https://lh4.googleusercontent.com/C37qdCh8qQASE2MazI6zXMe-iYowHsDUoUg8MI1T2cLVVfz5JIOvzG04z_gwtxjRae6xHnSc=w2880-h1598',
        },
        {
          name: 'David Mitchell',
          headshot: 'https://lh4.googleusercontent.com/GNCofZUrdtr0tNadP4Ezw6gJIpbRXLLTv-iwC44cIoMBDCjnH2EySVWnkOXcI-ngZ4pm8BtP=w2880-h1598',
        },
        {
          name: 'Jerome Scheuring',
          headshot: 'https://lh3.googleusercontent.com/Y27nEtmPav7p0w_eZz_zkGJvy-J2Kq9F2CMAbkcnYKGzrnBGrAGFf-s7VUrgkT152HopZbZK=w2880-h1598',
        },
      ],
    };
  },
};
</script>
