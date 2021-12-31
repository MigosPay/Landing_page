<template>
    <div class="q-px-lg q-gutter-y-lg" :style="$q.screen.gt.md ? 'padding: 0px 150px;' : ''">
        <div>
            <h3 class="text-bold"> Why Choose MigosPay</h3>
            <div class="text-grey-6">
                We leverage open banking to turn your bank account into your financial hub. <br />
                Control your financies like never before.
            </div>
        </div>
        <div class="row">
            <div class="col-sm-6 col-md-3 q-pa-md" v-for="choice in choiceArr" :key="choice.id">
                <div>
                    <q-avatar size="150px" font-size="52px">
                        <img :alt="choice.title" :src="choice.imgSrc" style="width: 100%;" >
                    </q-avatar>
                </div>
                <div>
                    <h4 class="text-bold text-grey-6"> {{ choice.title }} </h4>
                    <div class="text-grey-6">
                        {{ choice.content }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'WhyChooseMigos',
  data () {
    return {
      choiceArr: [
        { id: 0, imgSrc: require('../assets/img/banking_icon.png'), title: 'Online Banking', content: 'Our modern web and mobile applications allow you to keep track of your finances wherever you are in the world.' },
        { id: 1, imgSrc: require('../assets/img/budget_icon.png'), title: 'Simple Budgeting', content: 'See exactly where your money goes every month. Receive notifications when you\'re close to hitting your limits' },
        { id: 2, imgSrc: require('../assets/img/article/onboarding.jpg'), title: 'Fast Onboarding', content: 'We don\'t do branches. Open your account minutes online and start taking control of your finances right away.' },
        { id: 3, imgSrc: require('../assets/img/api_icon.png'), title: 'Open API', content: 'Manage your savings, investments, pensions and much more from one account. Tracking your money has never been easier' }
      ]
    }
  }
}
</script>
