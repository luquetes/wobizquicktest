<template>
  <div id="app" class="container-fluid">
    <div class="row">
      <div class="col-12 col-md-6 col-lg-4 p-0 ml-0 col">
        <LeftPanel />
      </div>
      <div class="col-lg-8 col-md-6 d-none d-md-block p-0 col">
        <RightPanel />
      </div>
    </div>
  </div>
</template>

<script>

import LeftPanel from './components/UI/leftPanel'
import RightPanel from './components/UI/rightPanel'

export default {
  name: 'App',
  components: { LeftPanel, RightPanel }
}
</script>

<style>

#app {
  box-sizing: border-box;
}

</style>
