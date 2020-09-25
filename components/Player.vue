<template>
    <div style="position:relative">
        <!--
        <audio id="player-radio" controls="controls" autoplay="" name="player-radio">
            <source :src="musicServer" type="audio/mpeg">
        </audio>
        -->
        <div id="player-radio" class="inline-flex absolute right-0 mt-4 w-1/3 h-20">
            <Live class="ml-8 mr-8" />
            <!-- serateur vertical -->
            <span class="border-solid border border-redProfond"></span>
            <div class="flex items-center" id="option-player">
                <Play class="ml-8 mr-8" />
                <Volume class="mr-8" />
                <MenuAudio />
            </div>
            
        </div>

    </div>
</template>

<script>
import Live from './player_modulo/Live'
import Play from './player_modulo/Play'
import Volume from './player_modulo/Volume'
import MenuAudio from './player_modulo/Menu_Audio'

    export default {
        name: 'Player',
        data() {
            return {
                musicInfo:  [
                    {
                        titleOfMusic : '',
                        artist: '',
                        cover: ''
                    }
                ],
            }
        },
        components: {
            Live,
            Play,
            Volume,
            MenuAudio
        },
        methods: {
            playlist() {
                return console.log('Playlost')
            }
        },
    }
</script>

<style lang="scss">
#player-radio {
    background: transparent;
    color: black;
    
    #option-player {
        
        #play, #pause, #volume , #menu-playlist{
            width: 2em;
            height: 2em;
        }

    }
    
}

</style>