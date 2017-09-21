<template>
  <div class="vml-default">
    <div class="vml-container">
      <h1 class="vml-section-title">
        <span class="vml-section-title__inner">#&nbsp;&nbsp;Our Speakers</span>
      </h1>
      <section class="vml-flex-row">
        <div class="vml-flex-item vml-speaker" v-for="speaker in speakers">
          <h2 class="vml-speaker__title">{{ speaker.name }}
            <br />
            <span class="vml-speaker__twitter">{{ speaker.twitter }}</span>
          </h2>
          <img class="vml-speaker__image" :src="speaker.headshot" />
        </div>
      </section>
      <h1>You can say:
        <br />"Alexa, ask KCDC what sessions are next?"
        <br />"Alexa, ask KCDC when is David Mitchell speaking?"
        <br />"Alexa, ask KCDC what sessions are about JavaScript?"</h1>
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
          headshot: 'https://github.com/andrewicarlson/kcdc-voice/raw/master/static/dinger.jpg',
          twitter: '@adazlian',
        },
        {
          name: 'Heather Downing',
          headshot: 'https://github.com/andrewicarlson/kcdc-voice/raw/master/static/downing.jpg',
          twitter: '@quorralyne',
        },
        {
          name: 'David Mitchell',
          headshot: 'https://github.com/andrewicarlson/kcdc-voice/raw/master/static/mitchell.jpg',
          twitter: '@davidmitchell',
        },
        {
          name: 'Jerome Scheuring',
          headshot: 'https://github.com/andrewicarlson/kcdc-voice/raw/master/static/scheuring.jpg',
          twitter: '@aethyrics',
        },
      ],
    };
  },
};
</script>
