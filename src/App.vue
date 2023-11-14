<template>
  <ScreenAdapter>
    <div class="page-container">
      <header class="page-header">
        <MainNav />
      </header>
      <main
        class="page-main"
      >
        <div class="touch-main ">
          <RouterView />
        </div>
      </main>
    </div>
  </ScreenAdapter>
</template>

<style lang="scss"  scoped>
.page-container {
  position: relative;
  z-index: 8;
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  pointer-events: none;
}
.page-header {
  position: relative;
  z-index: 12;
}
.page-main {
  position: relative;
  z-index: 10;
  flex: 1;
  pointer-events: none;
}
.touch-main {
  pointer-events: auto;
}
</style>
