<template>
  <div class="root">
    <agenda-items
      v-model="agenda"
      :useWindowAsScrollContainer="true"
      :useDragHandle="true"
    >
        <agenda-item
          v-for="(section, idx) in agenda"
          :item="section"
          :index="idx"
          :key="section.id"
        >
          <div class="agenda-item-title">
            <span v-handle class="handle"></span>
            <input
              @click="handleClick"
              v-model="section.title"
            >
          </div>
          <agenda-items
            v-model="section.items"
            :useWindowAsScrollContainer="true"
          >
            <agenda-item
              v-for="(agendaItem, ind) in section.items"
              :item="agendaItem"
              :index="ind"
              :key="agendaItem.id"
            >
              {{ agendaItem.title }}
              <agenda-items v-model="agendaItem.items">
                <agenda-item
                  v-for="(subItem, index) in agendaItem.items"
                  :item="subItem"
                  :index="index"
                  :key="subItem.id"
                >
                  {{ subItem.title }}
                </agenda-item>
              </agenda-items>
            </agenda-item>
          </agenda-items>
        </agenda-item>
    </agenda-items>
   </div>
</template>

<script>
import { HandleDirective } from 'vue-slicksort';

import AgendaItems from './AgendaItems';
import AgendaItem from './AgendaItem';


import SECTIONS from '../utils/data';

export default {
  name: 'Agenda',
  directives: { handle: HandleDirective },
  components: {
    AgendaItem,
    AgendaItems,
  },
  data() {
    return {
      agenda: [],
      subItems: [],
    };
  },
  mounted() {
    this.getAgenda();
  },
  methods: {
    handleClick(event) {
      // eslint-disable-next-line
      console.log(['handle click', event]);
    },
    getAgenda() {
      this.agenda = SECTIONS;
    },
  },
};
</script>
