<template>
  <aside id="sidebar-left" class="sidebar-left">
    <div class="sidebar-text">
      <h2>
        <router-link :to="{ name: user ? 'home' : 'welcome' }" >
          {{ appName }}
        </router-link>

        <a href="#" class="float-right text-primary" @click.prevent="logout">
          <fa icon="sign-out-alt" fixed-width />
        </a>
      </h2>
    </div>
    <div class="sidebar-header">
      <div class="sidebar-title">
        Navigation
      </div>
      <div class="sidebar-toggle d-none d-md-block" data-toggle-class="sidebar-left-collapsed" data-target="html"
           data-fire-event="sidebar-left-toggle">
        <i class="fas fa-bars" aria-label="Toggle sidebar"></i>
      </div>
    </div>
    <nav id="menu" class="nav-main" role="navigation">
        <ul class="nav nav-main">
          <!-- Authenticated -->
          <li v-if="user">
            <router-link :to="{ name: 'users' }" class="">
              <fa icon="user" fixed-width />
              {{ $t('users') }}
            </router-link>
          </li>
          <li v-if="user">
            <router-link :to="{ name: 'pages' }" class="">
              <fa icon="file" fixed-width />
              {{ $t('pages') }}
            </router-link>
          </li>
          <li v-if="user">
              <router-link :to="{ name: 'settings.profile' }" class="">
                <fa icon="cog" fixed-width />
                {{ $t('settings') }}
              </router-link>
          </li>
          <!-- Guest -->
          <template v-else>
            <li class="nav-item">
              <router-link :to="{ name: 'login' }" class="nav-link" active-class="active">
                {{ $t('login') }}
              </router-link>
            </li>
            <li class="nav-item">
              <router-link :to="{ name: 'register' }" class="nav-link" active-class="active">
                {{ $t('register') }}
              </router-link>
            </li>
          </template>
        </ul>

    </nav>

  </aside>
<!--  <nav class="navbar navbar-expand-lg navbar-light bg-white">-->
<!--    <div class="container">-->
<!--     -->

<!--      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarToggler" aria-controls="navbarToggler" aria-expanded="false">-->
<!--        <span class="navbar-toggler-icon" />-->
<!--      </button>-->

<!--    </div>-->
<!--  </nav>-->
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  data: () => ({
    appName: window.config.appName
  }),

  computed: mapGetters({
    user: 'auth/user'
  }),

  methods: {
    async logout () {
      // Log out the user.
      await this.$store.dispatch('auth/logout')

      // Redirect to login.
      this.$router.push({ name: 'login' })
    }
  }
}
</script>

<style scoped>
.profile-photo {
  width: 2rem;
  height: 2rem;
  margin: -.375rem 0;
}
</style>
