<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

function closeMenu() {
  menuOpen.value = false
}
</script>

<template>
  <header class="navbar-shell">
    <nav class="navbar-inner">
      <a
        class="navbar-brand"
        href="#home"
        @click="closeMenu"
      >
        Art, art, art, and more art!
      </a>

      <button
        class="menu-button"
        type="button"
        aria-label="Toggle navigation"
        :aria-expanded="menuOpen"
        @click="toggleMenu"
      >
        <span></span>
        <span></span>
      </button>

      <div
        class="navbar-links"
        :class="{ 'is-open': menuOpen }"
      >
        <a href="#part-one" @click="closeMenu">
          Part I
        </a>

        <a href="#part-two" @click="closeMenu">
          Part II
        </a>

        <a href="#reflection" @click="closeMenu">
          Final Reflection
        </a>

        <a href="#appendices" @click="closeMenu">
          Appendices
        </a>
      </div>
    </nav>
  </header>
</template>

<style scoped>
.navbar-shell {
  position: fixed;
  inset: 0 0 auto 0;
  z-index: 50;
  width: 100%;

  background: rgba(248, 245, 238, 0.94);
  border-bottom: 1px solid rgba(20, 20, 20, 0.12);
}

.navbar-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;

  width: min(
    var(--page-max-width),
    calc(100% - (var(--page-padding) * 2))
  );

  min-height: 72px;
  margin: 0 auto;
}

.navbar-brand {
  color: #171717;
  font-size: 1.08rem;
  font-weight: 800;
  text-decoration: none;
}

.navbar-links {
  display: flex;
  align-items: center;
  gap: 34px;
}

.navbar-links a {
  color: #171717;
  font-size: 0.92rem;
  font-weight: 700;
  text-decoration: none;

  transition: opacity 150ms ease;
}

.navbar-links a:hover {
  opacity: 0.55;
}

.menu-button {
  display: none;

  width: 40px;
  height: 40px;
  padding: 0;

  border: 0;
  background: transparent;

  cursor: pointer;
}

.menu-button span {
  display: block;
  width: 21px;
  height: 1.5px;
  margin: 5px auto;
  background: #171717;
}

@media (max-width: 820px) {
  .navbar-inner {
    position: relative;
    min-height: 64px;
  }

  .navbar-brand {
    max-width: calc(100% - 60px);
    font-size: 0.95rem;
  }

  .menu-button {
    display: block;
  }

  .navbar-links {
    position: absolute;
    top: 100%;
    left: calc(var(--page-padding) * -1);

    display: flex;
    flex-direction: column;
    align-items: stretch;

    width: calc(100% + (var(--page-padding) * 2));

    gap: 0;
    padding: 8px var(--page-padding) 12px;

    background: rgba(248, 245, 238, 0.98);
    border-bottom: 1px solid rgba(20, 20, 20, 0.12);

    opacity: 0;
    visibility: hidden;

    transform: translateY(-6px);

    transition:
      opacity 160ms ease,
      transform 160ms ease,
      visibility 160ms ease;
  }

  .navbar-links.is-open {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
  }

  .navbar-links a {
    padding: 14px 0;

    border-bottom: 1px solid rgba(20, 20, 20, 0.08);

    font-size: 0.95rem;
  }

  .navbar-links a:last-child {
    border-bottom: 0;
  }
}
</style>