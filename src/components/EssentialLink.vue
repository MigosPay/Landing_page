<template>
  <!-- <q-item clickable tag="a" target="_blank" :href="link" > -->
  <q-item clickable @click="visitPage(link)" >
    <q-item-section v-if="icon" avatar >
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>
        {{ caption }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
import { defineComponent } from 'vue'
import { mapActions } from 'vuex'

export default defineComponent({
  name: 'EssentialLink',
  props: {
    title: {
      type: String,
      required: true
    },

    caption: {
      type: String,
      default: ''
    },

    link: {
      type: String,
      default: '#'
    },

    icon: {
      type: String,
      default: ''
    }
  },
  methods: {
    ...mapActions('landingPage', ['scrollToNavLink']),
    visitPage (id) {
      const _ = this
      _.scrollToNavLink(id)
    }
  }
})
</script>
