<template>
    <div>
        <div
            @click="toggle"
            :class="{ 'active': isOpen}"
            id="burger">
            <button 
                type="button" 
                class="burger-button" 
                title="Menu">
                <span class="hidden"></span>
                <span class="burger-bar burger-bar--1 bg-redProfond"></span>
                <span class="burger-bar burger-bar--2 bg-redProfond"></span>
                <span class="burger-bar burger-bar--3 bg-redProfond"></span>
            </button>
        </div>
        <nav 
            id="menu"
            :class="{'active-menu' : isOpen , 'drop-menu': !isOpen}"
            class="w-2/12 h-screen flex-col bg-gradient-to-t bg-gradient-to-b from-red-600 to-red-500">
            
            <div id="menu_logo" class="flex justify-center pt-8">
                <img src="@/assets/menu/logo/Logo.png" alt="logo">
            </div>

            <div id="menu_link" class="flex flex-col justify-start items-start pl-8 mt-16">
                <li class="menu_headline pb-4"><NuxtLink to="/home">ACCUEIL</NuxtLink></li>
                <li class="menu_headline pb-4"><NuxtLink to="/articles">ARTICLES</NuxtLink></li>
                    <span class="menu_subtitle flex flex-col pb-4 ml-4">
                        <li class="pb-4"><NuxtLink to="">Musiques</NuxtLink></li>
                        <li class="pb-4"><NuxtLink to="">Technologies</NuxtLink></li>
                        <li class="pb-4"><NuxtLink to="">Coup de coeur</NuxtLink></li>
                    </span>
                <li class="menu_headline pb-4"><NuxtLink to="/poadcast">POADCASTS</NuxtLink></li>
                    <span class="menu_subtitle flex flex-col pb-4 ml-4">
                        <li class="pb-4"><NuxtLink to="">Émissions</NuxtLink></li>
                        <li class="pb-4"><NuxtLink to="">Les plus récents</NuxtLink></li>
                    </span>
                <li class="menu_headline pb-4"><NuxtLink to="/contact">NOUS CONTACTER</NuxtLink></li>
            </div>
        </nav>
        <div 
            v-if="isOpen" 
            class="block-opacity absolute transition delay-700 ease-in-out w-10/12 right-0 top-0 h-screen bg-blueDark bg-opacity-25">
        </div>
        
    </div>
</template>

<script>
    export default {
        name: 'Nav',
        data() {
            return {
                isOpen: false,
            }
        },
        methods: {
            toggle(){
                this.isOpen = !this.isOpen; 
            }
        },
    }
</script>

<style lang="scss">
.active-menu {
    display: flex!important;
    left: 0;
    top: 0;
    animation: showMenu 200ms ease-in-out;
}
.block-opacity {
    animation: showMenu 200ms ease-in-out;
}
/*
.drop-menu {
}
*/
#menu {
    display: none;
    position: absolute;
    z-index: 1000;
    #menu_logo {
        width: 100%;
        img {
            width: 70%;
            height: auto;
        }
    }
    #menu_link {
        
        .menu_headline , .menu_subtitle li {
            list-style: none;
            a {
                text-decoration: none;
                color: $font-color;
            }
        }
        .menu_headline {
            font-weight: bold;
            a {
                font-weight: bold;
                font-size: 0.9em;
            }
        }
        .menu_subtitle {
            li {
                a {
                    font-weight: lighter;
                    font-size: 0.7em;
                }
            }
        }
    }
    
}

button {
    cursor: pointer;
    &:focus {
    outline: 0;
}
}

    /* remove blue outline */


    .burger-button {
        /** */
        z-index: 1001!important;
        position: relative;
        left: 1em;
        top: 1em;
        height: 30px;
        width: 42px;
        display: block;
        border: 0;
        border-radius: 0;
        background-color: transparent;
        pointer-events: all;
        transition: transform .6s cubic-bezier(.165,.84,.44,1);
    }

    .burger-bar {
        position: absolute;
        top: 50%;
        right: 6px;
        left: 6px;
        height: 2px;
        width: auto;
        margin-top: -1px;
        transition: transform .6s cubic-bezier(.165,.84,.44,1),opacity .3s cubic-bezier(.165,.84,.44,1),background-color .6s cubic-bezier(.165,.84,.44,1);
    }

    .burger-bar--1 {
        -webkit-transform: translateY(-6px);
        transform: translateY(-6px);
    }

    .burger-bar--2 {
        transform-origin: 100% 50%;
        transform: scaleX(.8);
    }

    .burger-button:hover .burger-bar--2 {
        transform: scaleX(1);
    }

    .no-touchevents .burger-bar--2:hover {
        transform: scaleX(1);
    }

    .burger-bar--3 {
        transform: translateY(6px);
    }

    #burger.active .burger-button {
        transform: rotate(-180deg);
    }

    #burger.active .burger-bar--1 {
        transform: rotate(45deg);
        background-color: $active-color;
    }

    #burger.active .burger-bar--2 {
        opacity: 0;
    }

    #burger.active .burger-bar--3 {
        transform: rotate(-45deg);
        background-color: $active-color;
    }
    @keyframes showMenu {
        from{
            opacity: 0;

        }
        to{
            opacity: 1;
        }
    }

</style>