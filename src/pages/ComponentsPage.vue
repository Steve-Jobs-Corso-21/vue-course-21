<script setup lang="ts">
  import { ref } from 'vue';

  import RefValue from '../components/RefValue.vue';
  import ForComponent from '../components/ForComponent.vue';
  import ToDoList from '../components/ToDoList.vue';
  import TextComponent from '../components/TextComponent.vue';
  import ToDoListVModel from '../components/ToDoListVModel.vue';
  import MountedUnMounted from '../components/MountedUnMounted.vue';
  import ButtonComponent from '../components/ButtonComponent.vue';
  import SectionComponent from '../components/SectionComponent.vue';
  import ToDoListWithRef from '../components/ToDoListWithRef.vue';

  const mountToggle = ref<boolean>(false);

  const clickCounter = ref<number>(0);
</script>

<template>
  <h1>HOME</h1>

  <div class="container">
    <!-- REF -->
    <RefValue />

    <!-- FOR -->
    <ForComponent />
    <ToDoList />
    <ToDoListWithRef />
    <ToDoListVModel />

    <SectionComponent title="TEXT COMPONENT">
      <!-- TEXT COMPONENT -->
      <TextComponent :class="Math.random() > 0.5 ? 'red' : 'green'" />
      <TextComponent class="green" />
    </SectionComponent>

    <SectionComponent title="MOUNT & UNMOUNT">
      <!-- MOUNT & UNMOUNT -->
      <MountedUnMounted v-if="mountToggle" />
      <ButtonComponent
        :text="mountToggle ? 'hide' : 'show'"
        class="primary"
        @click="mountToggle = !mountToggle"
      />
    </SectionComponent>

    <SectionComponent title="BUTTON COMPONENT">
      <!-- BUTTON COMPONENT (DYNAMIC COMPONENT) -->
      <ButtonComponent
        text="+"
        class="primary"
        @click="console.log('click')"
        @buttonClick="clickCounter++"
      />
      <span>{{ clickCounter }}</span>
      <ButtonComponent
        text="-"
        class="secondary"
        @click="console.log('click 2')"
        @buttonClick="clickCounter--"
      />
    </SectionComponent>
  </div>
</template>
