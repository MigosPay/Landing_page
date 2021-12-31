<template>
    <div class="bg-grey-5" :class="$q.screen.gt.sm ? 'q-pa-lg' : ''">
      <div class="row">
        <div class="col-12 col-md-3 q-pa-lg">
          <div>
            <a class="_customLink" target="_blank" href=" https://www.facebook.com/migospay/">
              <q-chip color="blue"  text-color="white" icon="mdi-facebook"> Meta (Facebook) </q-chip>
            </a>
            <a class="_customLink" target="_blank" href="https://twitter.com/migospay">
              <q-chip color="blue" text-color="white" icon="mdi-twitter"> Twitter </q-chip>
            </a>
            <!-- <q-chip color="pink" text-color="white" icon="mdi-instagram"> Instagram </q-chip>
            <q-chip color="green" text-color="white" icon="mdi-whatsapp"> Whatsapp </q-chip> -->
          </div>
        </div>
        <div class="col-12 col-md-3 q-pa-lg">
          <q-list separator class="text-white">
            <q-item clickable v-ripple @click="visitPage('herosection')">
              <q-item-section> Home </q-item-section>
            </q-item>
            <q-item clickable v-ripple @click="visitPage('whychoosemigospay')">
              <q-item-section> About </q-item-section>
            </q-item>
            <q-item clickable v-ripple @click="visitPage('contactformsection')">
              <q-item-section> Contact </q-item-section>
            </q-item>
          </q-list>
        </div>
        <div class="col-12 col-md-3">
          <q-list separator class="text-white">
            <q-item clickable v-ripple @click="visitPage('latestarticle')">
              <q-item-section> Blog </q-item-section>
            </q-item>
            <q-separator />
          </q-list>
          <div class="text-center text-white">
            <h3 class="q-pa-md text-bold"> Available On</h3>
          </div>
          <div class="text-center">
            <a href="#" target="_blank">
              <img clickable v-ripple src="~assets/img/android.png" alt="Download Apk" class="_downloadApp" />
            </a>
            <a href="#" target="_blank">
              <img clickable v-ripple src="~assets/img/ios.png" alt="Download Ios" class="q-mb-sm _downloadApp" />
            </a>
          </div>
        </div>
        <div class="col-12 col-md-3 text-center q-pa-lg">
          <div class="_centerDiv">
            <q-btn no-caps class="q-px-lg q-py-md _gradientColor text-white" rounded dense label="Request Invite" style="width: 100%:" />
          </div>
        </div>
      </div>
    </div>
</template>

<style>
  ._centerDiv {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%)
  }
  ._downloadApp {
    width: 150px;
    cursor: pointer;
  }
</style>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'FooterSection',
  methods: {
    ...mapActions('landingPage', ['scrollToNavLink']),
    visitPage (id) {
      const _ = this
      _.scrollToNavLink(id)
    }
  }
}
</script>
