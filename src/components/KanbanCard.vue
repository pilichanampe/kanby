<template>
  <v-card class="bg-white shadow rounded px-3 pt-3 pb-5 border border-white">
    <v-chip
      v-if="task.type"
      small
      :color="badgeColor"
      class="white--text"
    >{{ task.type }}</v-chip>
      <v-card-title class="text-gray-700 font-semibold font-sans tracking-wide text-sm">
        {{task.title}}
      </v-card-title>
    <v-card-text>
      {{task.description}}
      <!-- <KanbanBadge v-show="task.type" :color="badgeColor">{{task.type}}</KanbanBadge> -->
    </v-card-text>
  </v-card>
</template>
<script>
// import KanbanBadge from "@/components/KanbanBadge";
export default {
  components: {
    // KanbanBadge
  },
  props: {
    task: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    badgeColor() {
      const mappings = {
        Design: "purple",
        "Feature Request": "teal",
        Backend: "blue",
        QA: "green",
        default: "teal"
      };
      return mappings[this.task.type] || mappings.default;
    }
  }
};
</script>
