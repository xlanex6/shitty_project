<template>
    <div class="flex justify-start items-start mt-24">
        <div class="w-5/12">
            <h2 class="text-4xl font-bold">{{ artiste }}</h2>
            <h4 class="text-2xl font-light">{{ title }}</h4>
            <p class="font-thin leading-7">
                {{ description }}
            </p>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: "Home",
        data() {
            return {
                artiste: '',
                title: '',
                description: '',
                ipadress: "adress_ip"
            }
        },
       mounted () {
           axios
                // query with get protocol on ipadress icecast2
                .get(this.ipadress)
                //Then retunr response on data object
                .then(resp => (
                    this.artiste = resp,//.data...
                    this.title = resp,//.data...
                    this.description = resp//.data...
                ))
                //catch error and return on console
                .catch(error => (
                    console.error(error)
                ))
       },
    }
</script>

<style lang="scss" scoped>

</style>