<template>
    <v-app dark>
        <v-container fill-height fluid>
            <v-row align="center" justify="center">
                <v-col cols="12">
                    <h1 class="text-center" v-if="error.statusCode === 404">{{ pageNotFound }}</h1>
                    <h1 class="text-center" v-else>{{ otherError }}</h1>
                    <div class="text-center">
                        <NuxtLink to="/">
                            Home page
                        </NuxtLink>
                    </div>
                </v-col>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
export default {
    layout: 'empty',
    props: {
        error: {
            type: Object,
            default: null
        }
    },
    data() {
        return {
            pageNotFound: '404 Not Found',
            otherError: 'An error occurred'
        }
    },
    head() {
        const title = this.error.statusCode === 404 ? this.pageNotFound : this.otherError
        return {
            title
        }
    }
}
</script>

<style scoped>
h1 {
    font-size: 20px;
}
</style>
