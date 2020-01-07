<template>
  <div class="page-wrapper">
    <sidebar/>

    <div class="content">
      <div class="container-fluid">
        <div class="page-title">
          <ol class="breadcrumb">
            <li class="breadcrumb-item active">Dashboard</li>
          </ol>
          <h2>Dashboard</h2>
          <div class="page-title-actions"></div>
        </div>
        <child/>

      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from '~/components/Sidebar'
export default {
  name: 'MainLayout',
  components: {
    Sidebar
  }
}
</script>
