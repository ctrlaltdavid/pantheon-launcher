<!--
//  CancelDownload.vue
//
//  Created by David Rowe on 14 Feb 2020.
//  Copyright 2020 Vircadia contributors.
//
//  Distributed under the Apache License, Version 2.0.
//  See the accompanying file LICENSE or http://www.apache.org/licenses/LICENSE-2.0.html
-->
<template>
    <v-dialog
        width="500"
        persistent
        v-model="showCancelDownload"
    >
        <v-card>
            <v-card-title
                class="headline"
                primary-title
                dark
            >
                <v-icon color="green" class="mr-2">mdi-comment-question</v-icon>
                Cancel Download?
            </v-card-title>
    
            <v-card-text>
                Do you want to cancel the download?
            </v-card-text>
    
            <v-divider></v-divider>

            <v-card-actions>
                <v-btn
                    color="primary"
                    @click="continueDownload(); $emit('hideDialog')"
                >
                    No
                </v-btn>
                <v-spacer></v-spacer>
                <v-btn
                    color="primary"
                    @click="cancelDownload(); $emit('hideDialog')"
                >
                    Yes
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
</template>


<script>
const { ipcRenderer } = require('electron');

export default {
    name: 'DownloadFailed',
	methods: {
        continueDownload: function () {
            // Nothing to do/
        },
        cancelDownload: function () {
            ipcRenderer.send('cancel-download');
        },
     },
    data: () => ({
        showCancelDownload: true,
    }),
};
</script>