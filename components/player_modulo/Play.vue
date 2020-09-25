<template>
    <div class="flex">
        <!--Play method-->
        <span @click="play">
            <!--Play icon-->
            <svg v-if="playerOn" class="fill-current text-redProfond dark:text-gray" id="play" x="0px" y="0px" viewBox="0 0 163.861 163.861" style="enable-background:new 0 0 163.861 163.861;" xml:space="preserve">
                <g>
                    <path d="M34.857,3.613C20.084-4.861,8.107,2.081,8.107,19.106v125.637c0,17.042,11.977,23.975,26.75,15.509L144.67,97.275c14.778-8.477,14.778-22.211,0-30.686L34.857,3.613z"/>
                </g>
            </svg>
                    <!--Pause icon-->
                    <svg v-else class="fill-current text-redProfond dark:text-gray" id="pause" x="0px" y="0px" viewBox="0 0 45.975 45.975" style="enable-background:new 0 0 45.975 45.975;" xml:space="preserve">
                        <g>
                            <path d="M13.987,0c-2.762,0-5,2.239-5,5v35.975c0,2.763,2.238,5,5,5s5-2.238,5-5V5C18.987,2.238,16.75,0,13.987,0z"/>
                            <path d="M31.987,0c-2.762,0-5,2.239-5,5v35.975c0,2.762,2.238,5,5,5s5-2.238,5-5V5C36.987,2.239,34.749,0,31.987,0z"/>
                        </g>
                    </svg>
        </span>
        <audio  autoplay>
            <source :src="urlRadio" type="audio/mpeg">
        </audio>
    </div>
</template>

<script>
    export default {
        name: "Play",
        data() {
            return {
                urlRadio : "http://82.165.206.27:8000/mazette", 
                playerOn: this.$store.state.play
            }
        },
        methods: {
            
            play() {
                this.$store.commit('toggle')
                /**
                 * source: https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement
                 */
                
                //We cacth HTML element audio
                let audio = document.querySelector('audio')

                if(!this.playerOn) {
                    //Every time we load the flux for direct
                    audio.load()
                    //After have load we play
                    audio.play()
                } else {
                    // Just for stop the flux
                    audio.pause()
                }
                
            },
            
            
        },
        
        mounted () {
            this.$store.commit('toggle')

            //https://developers.google.com/web/updates/2017/09/autoplay-policy-changes
            const audio = document.querySelector('audio')
            const promise = audio.play()

            if (promise !== undefined) {
                promise.then(_ => {
                    console.lg('autoplay marche')
                    // Autoplay started!
                    audio.autoplay = true
                    audio.load()
                }).catch(error => {
                    console.log('autoplay marche pas')
                    // Autoplay was prevented.
                    // Show a "Play" button so that user can start playback.
                    this.play()
                });
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>