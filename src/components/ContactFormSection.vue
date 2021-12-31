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
import { api } from 'boot/axios'
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
        _.notifyAlert('negative', 'mdi-alert', 'Please fill the form', 'center')
        return
      }
      const regex = /\S+@\S+\.\S+/
      if (!regex.test(_.email)) {
        _.notifyAlert('negative', 'mdi-alert', 'Please provide a valid email address', 'center')
        return
      }
      _.loading = true
      const mesObj = {
        name: _.name,
        email: _.email,
        message: _.message
      }
      api.post(
        'sendmail', JSON.stringify(mesObj)
      ).then((res) => {
        // Stop the loading here...
        _.loading = false
        const data = res.data
        if (data.error) {
          _.notifyAlert('negative', 'mdi-alert', data.message, 'center')
          return
        }
        _.notifyAlert('positive', 'mdi-information-outline', 'Message Sent Successfully', 'center')
        // Clear the form inputs
        _.name = ''
        _.email = ''
        _.message = ''
      }).catch((err) => {
        console.log(err)
        _.loading = false
        _.notifyAlert('negative', 'mdi-alert', 'Oops, please try again', 'center')
      })
    },
    notifyAlert (type, icon, msg, position) {
      const _ = this
      _.$q.notify({
        type: type,
        icon: icon,
        message: msg,
        position: position,
        time: 1000
      })
    }
  }
}
</script>
