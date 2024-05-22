<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-brown text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" alt="Shoes Store Logo">
          </q-avatar>
          <span> Shoes Store Yolanda</span>
        </q-toolbar-title>

        <q-btn dense flat round icon="shopping_cart" @click="toggleRightDrawer" />
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/home" label="Beranda" icon="home" />
        <q-route-tab to="/products" label="Produk" icon="shopping_bag" />
        <q-route-tab to="/contact" label="Kontak" icon="phone" />
      </q-tabs>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <q-list>
        <q-item-label header>Categories</q-item-label>
        <q-item clickable v-ripple @click="goToCategory('men')">
          <q-item-section avatar>
            <q-icon name="male" />
          </q-item-section>
          <q-item-section>Men</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="goToCategory('women')">
          <q-item-section avatar>
            <q-icon name="female" />
          </q-item-section>
          <q-item-section>Women</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="goToCategory('kids')">
          <q-item-section avatar>
            <q-icon name="child_care" />
          </q-item-section>
          <q-item-section>Kids</q-item-section>
        </q-item>
        <q-item clickable v-ripple @click="goToCategory('sale')">
          <q-item-section avatar>
            <q-icon name="local_offer" />
          </q-item-section>
          <q-item-section>Sale</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <q-list>
        <q-item-label header>Cart</q-item-label>
        <!-- Cart items would go here -->
        <q-item>
          <q-item-section>
            No items in cart
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md">
        <q-carousel
          animated
          v-model="slide"
          navigation
          infinite
          :autoplay="autoplay"
          arrows 
          transition-prev="slide-right"
          transition-next="slide-left"
          @mouseenter="autoplay = false"
          @mouseleave="autoplay = true"
        >
          <q-carousel-slide :name="1" class="carousel-slide" img-src="https://p-id.ipricegroup.com/media/Gita/Model_Sepatu_New_Balance.jpg" />
          <q-carousel-slide :name="2" class="carousel-slide" img-src="https://asset.kompas.com/crops/ABlxWITQQdplmsHe93h3UUbRp4Y=/0x0:1513x1009/780x390/data/photo/2022/07/18/62d529051ef4f.png" />
          <q-carousel-slide :name="3" class="carousel-slide" img-src="https://cf.shopee.co.id/file/id-11134207-7qula-ljf704pg56dyb9" />
          <q-carousel-slide :name="4" class="carousel-slide" img-src="https://www.static-src.com/wcsstore/Indraprastha/images/catalog/full//catalog-image/96/MTA-124940624/nike_sepatu-nike-dunk-low-pink-velvet-gs_full01.jpg" />
        </q-carousel>
      </div>
    </q-page-container>

    <q-footer elevated class="bg-brown text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <!-- Optional: You can add an avatar image here -->
          </q-avatar>
          <div>Shoes Store</div>
        </q-toolbar-title>
        <q-btn flat round dense icon="facebook" @click="openSocialMedia('facebook')" />
        <q-btn flat round dense icon="instagram" @click="openSocialMedia('instagram')" />
        <q-btn flat round dense icon="twitter" @click="openSocialMedia('twitter')" />
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const toggleRightDrawer = () => {
      rightDrawerOpen.value = !rightDrawerOpen.value
    }

    const goToCategory = (category) => {
      // Implement navigation to the category page
      console.log(`Navigating to ${category} category`)
    }

    const openSocialMedia = (platform) => {
      let url = ''
      switch (platform) {
        case 'facebook':
          url = 'https://facebook.com'
          break
        case 'instagram':
          url = 'https://instagram.com'
          break
        case 'twitter':
          url = 'https://twitter.com'
          break
      }
      window.open(url, '_blank')
    }

    return {
      leftDrawerOpen,
      toggleLeftDrawer,
      rightDrawerOpen,
      toggleRightDrawer,
      goToCategory,
      openSocialMedia,

      slide: ref(1),
      autoplay: ref(true)
    }
  }
}
</script>

<style scoped>
.bg-brown {
  background-color: brown !important;
}

.q-toolbar-title {
  display: flex;
  align-items: center;
}

.q-toolbar-title img {
  margin-right: 10px;
  height: 40px;
}

.q-tabs {
  margin-top: 10px;
}
</style>
