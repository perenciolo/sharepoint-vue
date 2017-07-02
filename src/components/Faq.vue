<template>
  <div class="faq">
    <collapse accordion is-fullwidth v-if="faqs">
      <collapse-item v-bind:title="faqs.title.rendered" >
        <div v-html="faqs.content.rendered"></div>
      </collapse-item>
    </collapse>
  </div>
</template>

<script>
import { Collapse, Item as CollapseItem } from 'vue-bulma-collapse'
import axios from 'axios'

export default {
  name: 'faq',
  data: () => ({
    faqs: [],
    errors: []
  }),
  components: {
    Collapse,
    CollapseItem
  },
  created () {
    axios.get(`http://amonp.org.br/wp-json/wp/v2/pages/331`)
    .then(response => {
      this.faqs = response.data
      console.log(this.faqs)
    })
    .catch(e => this.errors.push(e))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
@import '../mq'

</style>
