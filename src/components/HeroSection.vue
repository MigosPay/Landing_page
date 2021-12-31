<template>
    <!-- <div class="bg-white" style="height: 92.6vh;"> -->
    <div class="bg-white" style="">
        <div class="row">
            <div class="col-xs-12 col-sm-6 flex flex-center">
                <div class="q-pa-lg">
                    <div class="q-gutter-y-lg">
                        <h1 class="text-bold" :class="$q.screen.lt.md ? 'text-h3' : ''">
                            Next generation<br/>
                            digital banking
                        </h1>
                        <div>
                            Take you financial life onlline. Your easy bank account <br>
                            will be a one-stop-shop for spending saving, <br v-if="$q.screen.gt.xs">
                            budgeting, investing and much more.
                        </div>
                        <div>
                            <q-btn no-caps rounded class="q-px-lg _gradientColor" color="" label="Request Invite" />
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-xs-12 col-sm-6">
                <div class="">
                   <img alt="Hero Image" src="~assets/img/heroImage.png" style="width: 100%;" >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'HeroSection'
}
</script>
