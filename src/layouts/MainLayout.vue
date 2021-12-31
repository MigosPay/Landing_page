<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-white">
      <q-toolbar class="text-grey">
        <q-btn v-if="$q.screen.lt.sm" flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />
        <!-- <q-toolbar-title :style="$q.screen.lt.md ? 'max-width: 120px;' : ''"> -->
        <q-toolbar-title :style="$q.screen.lt.sm || $q.screen.gt.sm ? '' : 'max-width: 120px;'">
          <img alt="MigosPay logo" src="~assets/img/icon.png" style="width: 100px;" @click="visitPage('herosection')">
        </q-toolbar-title>
        <q-toolbar-title :style="$q.screen.lt.sm ? 'display: none' : 'display: block'">
          <q-btn flat no-caps class="q-px-md" rounded dense label="Home" @click="visitPage('herosection')" />
          <q-btn flat no-caps class="q-px-md" rounded dense label="About" @click="visitPage('whychoosemigospay')" />
          <q-btn flat no-caps class="q-px-md" rounded dense label="Contact" @click="visitPage('contactformsection')" />
          <q-btn flat no-caps class="q-px-md" rounded dense label="Blog" @click="visitPage('latestarticle')" />
          <!-- <q-btn flat no-caps class="q-px-md" rounded dense label="Carriers" /> -->
        </q-toolbar-title>
          <q-btn no-caps class="q-px-md _gradientColor text-white" rounded dense label="Request Invite" />
      </q-toolbar>
    </q-header>

    <q-drawer v-if="$q.screen.lt.sm" v-model="leftDrawerOpen"  bordered >
      <q-list>
        <q-item-label header >
          Essential Links
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container class="bg-grey-1">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<style>
  ._gradientColor {
    background: linear-gradient(to right, #19802d, #03c928);
  }
</style>

<script>
import EssentialLink from 'components/EssentialLink.vue'
import { mapActions } from 'vuex'

const linksList = [
  {
    title: 'Home',
    caption: 'Migospay.com',
    icon: 'home',
    link: 'herosection'
  },
  {
    title: 'About',
    caption: 'Get to know us more',
    icon: 'code',
    link: 'whychoosemigospay'
  },
  {
    title: 'Contact',
    caption: 'For more info',
    icon: 'chat',
    link: 'contactformsection'
  },
  {
    title: 'Blog',
    caption: 'Take a look at our journey so far',
    icon: 'record_voice_over',
    link: 'latestarticle'
  }
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
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
