<template>
    <v-row 
        justify="center" 
        align="center" 
        no-gutters
        style="min-height: 100vh"
    >
        <v-col 
            md="10" sm="12" 
        >      
            <v-row 
                align='center'
                justify='center'
                no-gutters
            >
                <v-col 
                    cols="12"
                    md="6"
                    lg="4"
                    v-for="(it, i) in list"
                    :key="it.title"
                >
                    
                    <v-card
                        :min-height="it.height"
                        :min-width="it.width"
                        :elevation="it.elevation"                        
                        :color="it.icon.color"
                        class="ma-md-1 ma-sm-auto"
                        :class="{ move_cards: moveCards}"
                        :style="{ transform: 'translateY(5rem)', 
                                    transition: 'transform 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28) ' + (0.05*i + 0.1) + 's'}"
                        tile
                    >
                        <div 
                            class="d-flex flex-no-wrap justify-space-between" 
                            :style="{ color : 'white' }"
                        >
                            <div>
                                <v-card-title>
                                    <TextAppearence
                                        :text="it.title"                                            
                                        :time=".75"
                                        :delay="0.1"
                                        from="b"
                                        :opacity="true"                                            
                                        :show="moveCards"
                                    />
                                </v-card-title>
                                <v-card-text class="d-flex flex-column">
                                    <TextAppearence
                                        class="display-1 mb-2 bold"
                                        :text="it.head"
                                        :time=".75"
                                        :delay="0.1"
                                        from="b"
                                        :opacity="true"    
                                        :show="moveCards"
                                    />
                                    <TextAppearence
                                        class="body-1 my-2"
                                        :style="{ fontSize : '1.5rem !important'}"
                                        :text="it.text"
                                        :time="0.75"
                                        :delay=".01"
                                        from="l"
                                        :opacity="true"   
                                        :show="moveCards"
                                    />
                                </v-card-text>
                            </div>
                            <v-icon
                                large
                                class="ma-5"
                                color="white"
                            >
                                {{ it.icon.name }}
                            </v-icon>
                        </div>                        
                    </v-card>                                                                                   
                </v-col>
            </v-row>
        </v-col>
    </v-row>        
</template>

<script>
import TextAppearence from '~/components/utils/TextAppearence.vue'

export default {
    name: 'About',
    props: {
        scroll: Number,
        height: Number
    },
    components: {
        TextAppearence
    },
    data() {
        return {
            temp: false,
            list: [
                {
                    title: 'Me',
                    head: 'HUMAN',
                    text: 'My name is Arseny Likhachev',
                    height: '10vh',
                    width: '10vw',
                    elevation: '10',
                    icon: {
                        name: 'mdi-account',
                        color: '#1E88E5'
                    }
                },
                {
                    title: 'Living',
                    head: 'PERM',
                    text: 'I am living in Perm',
                    height: '20vh',
                    width: '10vw',
                    elevation: '7',
                    icon: {
                        name: 'mdi-city',
                        color: '#FB8C00'
                    }
                },
                {
                    title: 'Skills',
                    head: 'FRONTEND',
                    text: 'Develop web-applicatons!',
                    height: '10vh',
                    width: '20vw',
                    elevation: '8',
                    icon: {
                        name: 'mdi-monitor-dashboard',
                        color: '#66BB6A'
                    }
                },
                {
                    title: 'Love',
                    head: 'CODING',
                    text: 'Code everything!',
                    height: '10vh',
                    width: '20vw',
                    elevation: '5',
                    icon: {
                        name: 'mdi-code-json',
                        color: '#00E5FF'
                    }
                },
                {
                    title: 'Wish',
                    head: 'TO IMPROVE',
                    text: 'Follow your dream!',
                    height: '20vh',
                    width: '20vw',
                    elevation: '6',
                    icon: {
                        name: 'mdi-book-open-page-variant',
                        color: '#5E35B1'
                    }
                }
            ]
        }
    },
    computed: {
        moveCards() {
            return (this.scroll/this.height) > 0.6;
        }
    }
}
</script>

<style lang="scss">
    .move_cards {
        transform: translateY(0) !important;
    }
</style>