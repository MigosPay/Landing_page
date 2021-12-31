<template>
    <div class="bg-white q-px-lg q-gutter-y-lg" :style="$q.screen.gt.md ? 'padding: 50px 150px;' : 'padding-top: 50px'">
        <div clas="q-pt-lg bg-red">
            <h3 class="text-bold"> Contact Us </h3>
        </div>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <div class="q-pa-md">
                    <div class="q-gutter-md">
                        <q-input filled v-model="name" label="Name:" />
                        <q-input filled v-model="email" label="Email:" />
                        <q-input filled type="textarea" v-model="message" label="Message:" />
                        <div class="text-center" style="width: 100%">
                            <q-btn no-caps rounded color="primary" class="q-px-lg" label="Submit" style="width: 80%" :loading="loading" @click="sendMessage()" >
                                <template #loading>
                                    <q-spinner-ball />
                                </template>
                            </q-btn>
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-xs-12 col-sm-6">
                <div class="text-center">
                   <img alt="Hero Image" src="~assets/img/contactForm.png" style="width: 100%;" >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ContactFormSection',
  data () {
    return {
      name: '',
      email: '',
      message: '',
      loading: false
    }
  },
  methods: {
    sendMessage () {
      const _ = this
      if (!_.name.length || !_.email.length || !_.message.length) {
        console.log('Please fill the form')
        return
      }
      _.loading = true
      const formData = new FormData()
      formData.append('name', _.name)
      formData.append('email', _.email)
      formData.append('message', _.message)
      _.$axios.post(
        'hello@migospay.com', formData
      ).then((res) => {
        // Stop the loading here...
        _.loading = false
        // Clear the form inputs
        _.name = ''
        _.email = ''
        _.message = ''
      }).catch((err) => {
        console.log(err)
        _.loading = false
      })
    }
  }
}
</script>
