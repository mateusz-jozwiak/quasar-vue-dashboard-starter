<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar class="text-white">
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title> Dashboard </q-toolbar-title>

        <div>
          <q-btn @click="toggleDarkMode" icon="fa-brands fa-github" round flat></q-btn>

        </div>

        <div>
          <q-btn @click="toggleDarkMode" icon="settings_brightness" round flat></q-btn>

        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above>
      <q-toolbar class="bg-primary">
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title> Dashboard </q-toolbar-title>
      </q-toolbar>
      <q-list>
        <q-item to="/" exact>
          <q-item-section avatar>
            <q-icon name="inbox" />
          </q-item-section>
          <q-item-section> Home </q-item-section>
        </q-item>

        <q-item to="/profile" exact>
          <q-item-section avatar>
            <q-icon name="settings" />
          </q-item-section>
          <q-item-section> About </q-item-section>
        </q-item>




        <q-expansion-item expand-icon-toggle expand-separator icon="perm_identity" label="Settings">


          <q-item to="/" exact>
            <q-item-section avatar>
              <q-icon name="outbox" />
            </q-item-section>
            <q-item-section> Profile </q-item-section>
          </q-item>

          <q-item to="/profile" exact>
            <q-item-section avatar>
              <q-icon name="settings" />
            </q-item-section>
            <q-item-section> Account </q-item-section>
          </q-item>

        </q-expansion-item>

        <q-expansion-item expand-icon-toggle expand-separator icon="signal_wifi_off" label="Content">
          <q-item to="/" exact>
            <q-item-section avatar>
              <q-icon name="outbox" />
            </q-item-section>
            <q-item-section> Link </q-item-section>
          </q-item>
        </q-expansion-item>

        <q-expansion-item expand-icon-toggle expand-separator icon="drafts" label="Other Stuff" header-class="">
          <q-item to="/" exact>
            <q-item-section avatar>
              <q-icon name="outbox" />
            </q-item-section>
            <q-item-section> Link </q-item-section>
          </q-item>

          <q-item to="/profile" exact>
            <q-item-section avatar>
              <q-icon name="settings" />
            </q-item-section>
            <q-item-section> About </q-item-section>
          </q-item>
        </q-expansion-item>




      </q-list>





    </q-drawer>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from 'quasar';

export default defineComponent({
  name: "MainLayout",

  components: {},

  setup() {
    const leftDrawerOpen = ref(false);
    const $q = useQuasar();
    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      toggleDarkMode() {
        $q.dark.toggle();
      },
    };
  },
});
</script>
