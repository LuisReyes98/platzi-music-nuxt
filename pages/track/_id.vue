<template lang="pug">
  .container(v-if="track.id")
    .columns
      .column.is-3.has-text-centered
        figure.media-left
          p.image
            img(:src="track.album.images[0].url")
          p.button-bar
            a.button.is-primary.is-large
              //- span.icon(@click="selectTrack") >

      .column.is-8
        .panel
          .panel-heading
            h1.title {{ trackTitle }}

          .panel-block
            article.media
              .media-content
                .content
                  ul(v-for="(v, k) in track" :key="k")
                    li
                      strong {{ k }}:&nbsp;
                      span {{ v }}

                //- nav.level
                //-   .level-left
                //-     a.level-item
</template>

<script>
import trackService from '~/plugins/track'
// import trackMixin from '@/mixins/track'

export default {
  // mixins: [ trackMixin ],
  asyncData ({ params }) {
    const id = params.id

    trackService.getById(id)
      .then((res) => {
        console.log(res)
        return { track: res }
      })
  },
  data () {
    return {
      track: {}
    }
  },
  head () {
    return {
      title: this.track.name
    }
  }
}
</script>

<style lang="scss" scoped>

.columns{
  margin: 20px;
}

.button-bar{
  margin-top: 20px;
}

</style>
