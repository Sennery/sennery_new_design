<template>
    <v-row 
        justify="center" 
        align="center" 
        no-gutters
        style="min-height: 100vh">
        <v-col 
            md="10" sm="12" >      
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
                    :key="it.title">
                    
                    <v-card
                            :min-height="it.height"
                            :min-width="it.width"
                            :elevation="it.elevation"                        
                            :color="it.icon.color"
                            class="ma-md-1 ma-sm-auto"
                            :class="{ move_cards: moveCards}"
                            :style="{ transform: 'translateY(' + (2*i + 0.5) + 'rem)', 
                                      transition: 'transform ' + (0.05*i + 0.1) + 's ease-in'}"
                            ripple
                            tile
                            >
                            <div class="d-flex flex-no-wrap justify-space-between" :style="{ color : 'white' }">
                                <div>
                                    <v-card-title>
                                        {{ it.title }}
                                    </v-card-title>
                                    <v-card-text>
                                        <p class="display-1">{{ it.head }}</p>
                                        <p class="body-1" :style="{ fontSize : '1.5rem !important'}"> {{ it.text }} </p>
                                    </v-card-text>
                                </div>
                                <v-icon
                                    large
                                    class="ma-5"
                                    color="white">
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
export default {
    name: 'About',
    props: {
        scroll: Number,
        height: Number
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
                    elevation: '10',
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
                    elevation: '10',
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
                    elevation: '10',
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
                    elevation: '10',
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