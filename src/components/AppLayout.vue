<template>
    <div class="layout">
        <header style="text-align: center;">
            <slot name="header" />
        </header>
        <main >
            <slot />
        </main>
        <footer>
            <slot name="footer" />
        </footer>
    </div>
</template>
  
  <script>
  export default {};
  </script>
  
  <style scoped>
  .layout {
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  .layout header,
  .layout footer {
    background: #41b883;
    color: white;
    padding: 1rem;
    flex: 0 0 auto;
  }
  .layout main {
    flex: 1 1 auto;
    height: 90vh;
  }
  </style>