<template>
    <div class="flex">
        <span id="info-music" class="mt-1 flex justify-start flex-col items-center">
            <h2 id="artist" class="text-white dark:text-gray">Artiste</h2>
            <h4 id="title-music" class="text-white dark:text-gray">Title of music</h4>
        </span>
    </div>
</template>

<script>
    export default {
        name: "HeadlineAlbum",
    }
</script>

<style lang="scss">
#info-music {
        
        h2 {
             font-size: 1em;
        }
        h4 {
            font-size: .8em;
            font-weight: lighter;
        }
    }
</style>