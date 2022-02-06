<template>
  <div>
    <NavBar />
    <IESJakLinksCopy />
    <IESJakLinks />
    <IESJakBottomStuff />
  </div>
</template>

<script>
import NavBar from '~/components/NavBar.vue'
import IESJakBottomStuff from '~/components/IESJakBottomStuff.vue'
import IESJakLinksCopy from '~/components/IESJakLinksCopy.vue'
export default {
  name: 'IndexPage',
  components: { NavBar, IESJakBottomStuff, IESJakLinksCopy },
}
</script>
