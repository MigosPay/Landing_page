<template>
    <div class="q-px-lg q-gutter-y-lg" :style="$q.screen.gt.md ? 'padding: 0px 150px;' : ''">
        <div class="row ">
            <div class="col-xs-6 col-sm-3" v-for="flag in countryFlagArr" :key="flag.id">
                <q-card class="my-card">
                    <q-img :src="flag.imgSrc">
                        <div class="absolute-bottom text-subtitle2 text-center text-bold">
                            {{ flag.name }}
                        </div>
                    </q-img>
                </q-card>
            </div>
        </div>
    </div>
</template>

<style>
    .my-card{
        width: 100%;
        max-width: 250px;
    }
</style>

<script>
export default {
  name: 'Countries',
  data () {
    return {
      countryFlagArr: [
        { id: 0, name: 'CAMEROON', imgSrc: require('../assets/img/flags/cameroon.jpg') },
        { id: 1, name: 'RWANDA', imgSrc: require('../assets/img/flags/rwanda.jpg') },
        { id: 2, name: 'UK', imgSrc: require('../assets/img/flags/uk.jpg') },
        { id: 3, name: 'USA', imgSrc: require('../assets/img/flags/usa.jpg') }
      ]
    }
  }
}
</script>
