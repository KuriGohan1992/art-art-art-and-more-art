<script setup>
import { onBeforeUnmount, onMounted } from 'vue'

defineProps({
  src: {
    type: String,
    required: true,
  },
  alt: {
    type: String,
    default: '',
  },
})

const emit = defineEmits(['close'])

function handleKeydown(event) {
  if (event.key === 'Escape') {
    emit('close')
  }
}

onMounted(() => {
  document.body.style.overflow = 'hidden'
  window.addEventListener('keydown', handleKeydown)
})

onBeforeUnmount(() => {
  document.body.style.overflow = ''
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <Teleport to="body">
    <div
      class="modal-backdrop"
      @click.self="$emit('close')"
    >
      <button
        class="modal-close"
        type="button"
        aria-label="Close image"
        @click="$emit('close')"
      >
        ×
      </button>

      <img
        :src="src"
        :alt="alt"
        class="modal-image"
      />
    </div>
  </Teleport>
</template>

<style scoped>
.modal-backdrop {
  position: fixed;
  inset: 0;

  z-index: 9999;

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 36px;

  background:
    rgba(15, 15, 15, 0.88);
}

.modal-image {
  display: block;

  max-width: min(1400px, 94vw);
  max-height: 90vh;

  width: auto;
  height: auto;

  object-fit: contain;

  border: 2px solid white;

  box-shadow:
    12px 12px 0
    rgba(255, 255, 255, 0.22);
}

.modal-close {
  position: fixed;

  top: 22px;
  right: 28px;

  width: 48px;
  height: 48px;

  border: 2px solid white;

  color: white;
  background: #171717;

  font-size: 2rem;
  line-height: 1;

  cursor: pointer;
}

@media (max-width: 760px) {
  .modal-backdrop {
    padding: 18px;
  }

  .modal-close {
    top: 12px;
    right: 12px;

    width: 42px;
    height: 42px;
  }

  .modal-image {
    max-width: 96vw;
    max-height: 88vh;
  }
}
</style>