<template>
  <q-page class="">
    <div id="herosection">
      <HeroSection />
    </div>
    <div class="q-py-lg q-my-lg"></div>
    <div id="whychoosemigospay">
      <WhyChooseMigosPay />
    </div>
    <div class="q-py-lg q-my-lg"></div>
    <div id="countries">
      <Countries />
    </div>
    <div class="q-py-lg q-my-lg"></div>
    <div id="latestarticle">
      <LatestArticles />
    </div>
    <div class="q-py-lg q-my-lg"></div>
    <div id="contactformsection">
      <ContactFormSection />
    </div>
    <FooterSection />
  </q-page>
</template>

<script>
import HeroSection from 'components/HeroSection.vue'
import WhyChooseMigosPay from 'components/WhyChooseMigosPay.vue'
import Countries from 'components/Countries.vue'
import LatestArticles from 'components/LatestArticles.vue'
import ContactFormSection from 'components/ContactFormSection.vue'
import FooterSection from 'components/FooterSection.vue'
import { mapGetters } from 'vuex'
import { scroll } from 'quasar'
const { getScrollTarget, setVerticalScrollPosition } = scroll

export default {
  name: 'LandingPage',
  computed: {
    ...mapGetters('landingPage', ['getClickedNavLink'])
  },
  components: {
    HeroSection,
    WhyChooseMigosPay,
    Countries,
    LatestArticles,
    ContactFormSection,
    FooterSection
  },
  methods: {
    scrollToElement (el) {
      const element = document.getElementById(el)
      const target = getScrollTarget(element)
      const offset = element.offsetTop
      const duration = 100
      setVerticalScrollPosition(target, offset, duration)
    }
  },
  watch: {
    getClickedNavLink (id) {
      const _ = this
      if (id.length) {
        _.scrollToElement(id)
      }
    }
  }
}
</script>
