<template>
  <div class='sidebar-container dark-black'>
    <div @click="tabSwitch('')" title='Dashboard'>
      <img class="logo-icon-small cursor-pointer" src="../../assets/images/titania-logo-clean.svg">
    </div>
    <div class='margin-top-20 cursor-pointer' title='dApps Console' @click="tabSwitch('dappsconsole')" >
      <img v-if="currentTab('dappsconsole')" class="tab-label" src="../../assets/images/icon-boxes-b.svg">
      <img v-else class="tab-label" src="../../assets/images/icon-boxes-a.svg">
    </div>
    <div @click="tabSwitch('stats')" title='dApps Stats' class='cursor-pointer'>
      <img v-if="currentPage == 'stats'" class="tab-label" src="../../assets/images/icon-server-b.svg">
      <img v-else class="tab-label" src="../../assets/images/icon-server-a.svg">
    </div>
    <div @click="tabSwitch('threads')" title='Threads' class='cursor-pointer'>
      <img v-if="currentTab('threads')" class="tab-label" src="../../assets/images/icon-thread-b.svg">
      <img v-else class="tab-label" src="../../assets/images/icon-thread-a.svg">
    </div>
    <div @click="tabSwitch('dappshub')" title='dApps Hub' class='cursor-pointer'>
      <img v-if="currentTab('dappshub')" class="tab-label" src="../../assets/images/icon-hub-b.svg">
      <img v-else class="tab-label" src="../../assets/images/icon-hub-a.svg">
    </div>
    <div @click="tabSwitch('settings')" title='Settings' class='cursor-pointer settings-tab'>
      <img v-if="currentTab('settings')" class="tab-label" src="../../assets/images/settings-white.svg">
      <img v-else class="tab-label" src="../../assets/images/settings.svg">
    </div>
    <div @click="reboot()" title='Reboot OS' class='cursor-pointer reboot-tab'>
      <img class="tab-label" src="../../assets/images/icons-restart.svg">
    </div>
  </div>
</template>

<script>
import router from '../../router'

export default {
  name: 'sidebarParent',
  computed: {
    currentPage: {
      get: function () {
        return this.$store.state.currentPage
      },
      set: function (page) {
        this.$store.state.currentPage = page
      }
    }
  },
  methods: {
    tabSwitch (tabname) {
      if (tabname.length === 0) {
        router.push('/')
        this.$store.dispatch('switchDrilldown', 'dashboard')
      } else {
        router.push('/' + tabname)
        this.$store.dispatch('switchDrilldown', tabname)
        this.currentPage = tabname
      }
    },
    currentTab (tabname) {
      return this.currentPage === tabname
    },
    reboot () {
        this.$store.dispatch('rebootSystem')
    }
  }
}
</script>
