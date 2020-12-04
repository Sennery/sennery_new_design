<template>
    <v-row 
        justify="start" 
        align="center" 
        no-gutters 
        style="height: 100vh; overflow: hidden;" 
        elevation="10"
    >
        <v-col 
            justify="center" 
            align="center" 
            class="pa-0" 
            sm="12" md="4"
        >
            <v-card
                color="#1E88E5"
                elevation="5"
                max-height="50vh"
                min-width="50vw"
            >
                <div class="d-flex flex-no-wrap justify-space-between bold">
                    <p 
                        class="contact-h first" 
                        :class="{ translateHeaders: activate }"
                    >
                        CONTACT
                    </p>                                
                    <p 
                        class="contact-h second d-none d-md-flex" 
                        :class="{ translateHeaders: activate }"
                    >
                        ME, FRIEND
                    </p>

                    <v-sheet
                        class="sheet"
                        max-width="50%"
                    >
                        <v-row 
                            no-gutters
                            class="mr-0"
                        >
                            <v-col 
                                class="ma-2 pa-0 contact_card"
                                cols="auto"
                                v-for="(it, i) in contacts"
                                :key="it.title"
                            >

                                <v-card
                                    tile
                                    ripple
                                    min-height="10vh"
                                    min-width="30rem" 
                                    elevation="3"                               
                                    :class="{ translateContacts: activate }"
                                    :style="{transform: 'translateY(2rem) scale(0.9)', 
                                            transition: 'transform 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28) ' + (0.05*i + 0.1) + 's'}"
                                >

                                    <v-card-title
                                        class="display-1"
                                    >
                                        <TextAppearence
                                            :text="it.title"                                            
                                            :time=".75"
                                            :delay="0.1"
                                            from="b"
                                            :opacity="true"                                            
                                            :show="activate"
                                        />
                                    </v-card-title>
                                    <v-icon
                                        large
                                        class="ma-md-5 ma-xs-3"
                                        :color="it.icon.color"
                                    >
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
</template>

<script>
import TextAppearence from '~/components/helpers/TextAppearence.vue'

export default {
    props: {
        scroll: Number,
        height: Number
    },
    components: {
        TextAppearence
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
        activate() {
            return (this.scroll/this.height) > 0.45
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
        transform: translateY(-7.5rem) scale(1) !important;
    }

    .translateHeaders {
        transform: rotateZ(-90deg)
                translateX(0)
                scale(1) !important;
    }
    
    .contact-h {
        position: absolute;
        font-size: 10rem;
        transform-origin: 0%;
        transform: rotateZ(-90deg)
                translateX(-7.5rem)
                scale(0.95);
        color: white;        
        bottom: -40%;
        white-space: nowrap;
        text-shadow: -3px 0px 3px rgba(0, 0, 0, 0.2), -3px 0px 4px rgba(0, 0, 0, 0.14), -1px 0px 8px rgba(0, 0, 0, 0.12);

        &.first {
            left: 25%;
            transition: transform 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28);
        }

        &.second {
            left: 40%;
            transition: transform 0.3s cubic-bezier(0.18, 0.89, 0.32, 1.28) 0.1s;
        }
    }

    .contact_card {
        transition: transform 0.2s ease;

        &:hover{
            transform: translateX(-0.5rem);
        }        
    }

    @media screen and (max-device-width: 600px) {
        .sheet {
            right: -40%;
        }
    }
</style>