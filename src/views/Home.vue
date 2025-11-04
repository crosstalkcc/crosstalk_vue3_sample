<script setup lang="ts">
import { ref, watch } from 'vue';
import ArticleID from '../components/ArticleID.vue';
import ArticleURL from '../components/ArticleURL.vue';
import LiveTV from '../components/LiveTV.vue';
import { useTheme } from 'vuetify'

const theme = useTheme()

const selectedIndex = ref(0);
const isLight = ref(true);

watch(isLight, (islight, _)=> {
    if(islight) theme.change('light')
    else theme.change('dark');
});
</script>

<template>
    <v-layout class="rounded rounded-md border">
        <v-app-bar title="CrossTalk Sample">
            <template v-slot:append>
                <v-switch color="primary" class="mx-2" v-model="isLight" :label="isLight ? 'Light Theme (On)' : 'Light Theme (Off)'" inset />
            </template>
        </v-app-bar>

        <v-navigation-drawer>
            <v-list nav>
                <v-list-item :active="selectedIndex==0" title="Comments with ID" link @click="selectedIndex = 0" />
                <v-list-item :active="selectedIndex==1" title="Comments with URL" link @click="selectedIndex = 1" />
                <v-list-item :active="selectedIndex==2" title="Live Chat with Video" link @click="selectedIndex = 2" />
                <v-divider />

                <v-list-item link href="https://crosstalk.cc" target="_blank">crosstalk.cc</v-list-item>
            </v-list>
        </v-navigation-drawer>

        <v-main class="d-flex align-center justify-center">
            <v-container>
                <v-sheet border="dashed md" color="surface-light" rounded="lg" width="100%">
                    <ArticleID v-if="selectedIndex == 0" :isLight="isLight" />
                    <ArticleURL v-if="selectedIndex == 1" :isLight="isLight" />
                    <LiveTV v-if="selectedIndex == 2" :isLight="isLight" />
                </v-sheet>
                
                <v-btn class="my-2 text-none" href="https://www.npmjs.com/package/crosstalk-comments-livechat-vue3" target="_blank" variant="flat" color="primary">crosstalk-comments-livechat-vue3 on NPM</v-btn>
                <v-btn class="ma-2 text-none" href="https://crosstalk.cc" target="_blank" variant="flat" color="primary">crosstalk.cc</v-btn>
            </v-container>
        </v-main>
    </v-layout>
</template>