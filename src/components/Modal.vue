<script setup>
import useFocusTrap from '../composables/useFocusTrap';

defineEmits(['close']);
defineProps({
  isModalOpen: Boolean,
});

const { trapRef } = useFocusTrap();

const submitForm = () => {
  alert('Form submitted!');
};
</script>

<template>
  <transition name="fade">
    <div v-if="isModalOpen" :class="$style.overlay"></div>
  </transition>
  <transition name="slide-fade">
    <div v-if="isModalOpen" :class="$style.modalContainer">
      <div :class="$style.modal" ref="trapRef" role="dialog">
        <header :class="$style.formHeadline">Login</header>
        <main>
          <form>
            <div :class="$style.formRow">
              <label for="email">Email</label>
              <input type="email" name="email" id="email" />
            </div>
            <div :class="$style.formRow">
              <label for="email">Password</label>
              <input type="password" name="password" id="password" />
            </div>

            <div :class="$style.formActions">
              <button @click.prevent="$emit('close')">Cancel</button>
              <button @click.prevent="submitForm">Submit form</button>
            </div>
          </form>
        </main>
      </div>
    </div>
  </transition>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease-in-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(2rem);
  opacity: 0;
}
</style>

<style module>
.overlay {
  background: rgba(0, 0, 0, 0.3);
  position: fixed;
  inset: 0;
}

.modalContainer {
  position: fixed;
  inset: 0;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 25rem;
  margin: 0 auto;
  padding: 2rem;
  z-index: 10;
  background-color: white;
  transform: translateY(-2rem);
}

.formHeadline {
  font-size: 1.6rem;
  margin-bottom: 2rem;
}

.formRow {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin-bottom: 1.5rem;
}

.formRow label {
  margin-bottom: 0.5rem;
  display: block;
  width: 100%;
  text-align: left;
  flex-basis: 100%;
}

.formRow input {
  flex-basis: 100%;
  padding: 0.5rem 0.75rem;
}

.formActions {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 1rem;
}
</style>
