<template>
    <div id="container" class='landing-background'>
       <div class="center-aligned">
        <div class="loader-ring zoomOut">
            <div class="loader-ring__logo zoomIn3">
                <img src="../../assets/images/titania-logo-clean.svg" alt="Titania logo" class="pulse">
            </div>
            <div class="loader-ring__inner zoomIn2">
                <div class="rotating2"></div>
            </div>
            <div class="loader-ring__outer zoomIn1">
                <div class="rotating"></div>
            </div>
        </div>
        <div class="margin-20-center zoomOut">
            <div v-if="this.$route.params.reboot" class="zoomIn2 large-fontsize">TitaniaOS has just been restarted</div>      
            <div v-if="this.$route.params.reboot" class="zoomIn2 large-fontsize">This interface will be back online in a few minutes</div>      
            <div v-else class="zoomIn2 large-fontsize">Loading, please wait...</div>        
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'landingpage',
  created: function () {
    if (this.$route.params.reboot) {
        setTimeout(function () {
            location.reload()
        }, 8000)
    }
  }
}
</script>
