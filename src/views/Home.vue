<template>
  <div class="home">
    <div id = "cards" class = "d-flex justify-content-center">
      <div v-for="project in projects" :key="project.id" class="card" style="width: 18rem;">
        <div class="card-body">
          <h5 class="card-title">
            <router-link :to="'/'+project.component">{{project.component}}</router-link>
          </h5>
          <p class="card-text">{{project.description}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'home',
  data() {
    return {
      projects: [
        {
          id: 1,
          component: 'OneDimensionalMap',
          description: 'A quick sample of converging resonant series over long and short durations',
        },
      ],
    }
  },
}
</script>
