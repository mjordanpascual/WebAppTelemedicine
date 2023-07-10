<script setup>
import routes from "src/router/routes.js";

import { computed } from "vue";

const tabs = computed(() => {
  const layout = routes.filter((item) => {
    return item.path === "/auth";
  });

  const children = layout.map((item) => {
    return item.children;
  });

  return children[0];
});
</script>

<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img
              src="https://scontent.fmnl33-1.fna.fbcdn.net/v/t39.30808-6/298566118_110154615133234_6965500980030156126_n.jpg?_nc_cat=108&cb=99be929b-59f725be&ccb=1-7&_nc_sid=09cbfe&_nc_eui2=AeE-kYXJLgOJ_q0Lg7-sMacxAsFDHxZ-RPoCwUMfFn5E-h7RtXypQ7jcmDPPBdATQqi8fgvUmJ_RMLgEILlhFlDa&_nc_ohc=QvEjMnBsJF4AX8ESRss&_nc_ht=scontent.fmnl33-1.fna&oh=00_AfAws5hyhzVfqVoVzqQ4aXvRCPxfbzZHab-z4EBsYIqMyA&oe=64B01D68"
            />
          </q-avatar>
          Web App Telemedicine
        </q-toolbar-title>
      </q-toolbar>

      <q-tabs align="center">
        <q-route-tab
          v-for="tab in tabs"
          :key="tab.path"
          :to="'/auth/' + tab.path"
          :label="tab.name"
        />
      </q-tabs>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>
