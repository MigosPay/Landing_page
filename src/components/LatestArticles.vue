<template>
    <div class="q-px-lg q-gutter-y-lg" :style="$q.screen.gt.md ? 'padding: 0px 150px;' : ''">
        <div>
            <h3 class="text-bold"> Latest Articles </h3>
        </div>
        <div class="row">
            <div class="col-sm-6 col-md-3 q-pa-md" v-for="article in latestArticleArr" :key="article.id">
                <q-card class="">
                    <img :src="article.imgSrc">

                    <q-card-section>
                        <div class="text-h5 text-bold"> {{ article.title }} </div>
                        <!-- <div class="text-subtitle2">by John Doe</div> -->
                    </q-card-section>

                    <q-card-section class="q-pt-none">
                        {{ article.content }}
                    </q-card-section>
                </q-card>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'LatestArticles',
  data () {
    return {
      latestArticleArr: [
        { id: 0, imgSrc: require('../assets/img/article/banking.jpg'), title: 'Online Banking', content: 'Our modern web and mobile applications allow you to keep track of your finances wherever you are in the world.' },
        { id: 1, imgSrc: require('../assets/img/article/budgeting.jpg'), title: 'Simple Budgeting', content: 'See exactly where your money goes every month. Receive notifications when you\'re close to hitting your limits' },
        { id: 2, imgSrc: require('../assets/img/article/onboarding.jpg'), title: 'Fast Onboarding', content: 'We don\'t do branches. Open your account minutes online and start taking control of your finances right away.' },
        { id: 3, imgSrc: require('../assets/img/article/api.jpg'), title: 'Open API', content: 'Manage your savings, investments, pensions and much more from one account. Tracking your money has never been easier' }
      ]
    }
  }
}
</script>
