<template>
    <v-row no-gutters>
        <v-col  justify="center" align="center" class="pa-0">
            <v-row 
                justify="start" 
                align="center" 
                no-gutters 
                style="height: 100vh; overflow: hidden;" 
                elevation="10">
                <v-col sm="12" md="4">

                    <v-card
                        color="#1E88E5"
                        elevation="5"
                        max-height="50vh"
                        min-width="50vw"
                    >
                        <div class="d-flex flex-no-wrap justify-space-between">
                            <p 
                                class="contact-h first" 
                                :class="{ translateHeaders: contactsTranslateY }">
                                CONTACT
                            </p>                                
                            <p 
                                class="contact-h second d-none d-md-flex" 
                                :class="{ translateHeaders: contactsTranslateY }">
                                ME, FRIEND
                            </p>

                            <v-sheet
                                class="sheet"
                                max-width="50%"
                                >
                                <v-row 
                                    no-gutters
                                    class="mr-0">
                                    <v-col 
                                        class="ma-2 pa-0 contact_card"
                                        cols="auto"
                                        v-for="(it, i) in contacts"
                                        :key="it.title">

                                        <v-card
                                            tile
                                            ripple
                                            min-height="10vh"
                                            min-width="30rem" 
                                            elevation="5"                               
                                            :class="{ translateContacts: contactsTranslateY }"
                                            :style="{transform: 'translateY(2rem)', 
                                                    transition: 'transform ' + (0.05*i + 0.1) + 's ease-in'}">

                                            <v-card-title
                                                class="display-1">
                                                {{ it.title }}
                                            </v-card-title>
                                            <v-icon
                                                large
                                                class="ma-md-5 ma-xs-3"
                                                :color="it.icon.color">
                                                {{ it.icon.name }}
                                            </v-icon>
                                        </v-card>
                                    </v-col>
                                </v-row>
                            </v-sheet>
                        </div>                            
                    </v-card>
                </v-col>
            </v-row>                               
        </v-col>        
    </v-row>
</template>

<script>
export default {
    props: {
        scroll: Number,
        height: Number
    },
    data() {
        return {
            contacts: [
                {
                    title: 'VK',
                    ref: '',
                    icon: {
                        name: 'mdi-vk',
                        color: ''
                    }
                },
                {
                    title: 'Telegram',
                    ref: '',
                    icon: {
                        name: 'mdi-telegram',
                        color: ''
                    }
                    
                },
                {
                    title: 'GitHub',
                    ref: '',
                    icon: {
                        name: 'mdi-github',
                        color: ''
                    }
                    
                },
                {
                    title: 'Mail',
                    ref: '',
                    icon: {
                        name: 'mdi-at',
                        color: ''
                    }
                    
                }
            ]
        }
    },
    computed: {
        contactsTranslateY() {
            return (this.scroll/this.height) > 0.45
        },
        theme(){
            return (this.$vuetify.theme.dark) ? 'dark' : 'light'
        }
    }
}
</script>

<style lang="scss" scoped>
    .sheet {
        position: relative; 
        right: -90%;    
        background: transparent !important;
    }

    .translateContacts {
        transform: translateY(-7.5rem) !important;
    }

    .translateHeaders {
        transform: rotateZ(-90deg)
                translateX(0) !important;
    }
    
    .contact-h {
        position: absolute;
        font-size: 10rem;
        transform-origin: 0%;
        transform: rotateZ(-90deg)
                translateX(-7.5rem);
        color: white;        
        bottom: -40%;
        white-space: nowrap;

        &.first {
            left: 25%;
            transition: transform 0.3s ease-in;
        }

        &.second {
            left: 40%;
            transition: transform 0.35s ease-in;
        }
    }

    .contact_card {
        transition: transform 0.2s ease;

        &:hover{
            transform: skewX(0.5deg) translateX(-0.5rem);
        }        
    }

    @media screen and (max-device-width: 600px) {
        .sheet {
            right: -40%;
        }
    }
</style>