<template>
  <section v-if="isLoading" class="section">
    <b-tabs type="is-toggle" expanded>
      <b-tab-item label="All">
        <div v-for="luanch in launches" :key="luanch.id">
          <Card
            :title="luanch.name"
            :upcoming="luanch.upcoming"
            :success="luanch.success"
          >
          </Card>
        </div>
      </b-tab-item>
      <b-tab-item label="Luanches">
        <div v-for="luanch in launches" :key="luanch.id">
          <Card
            v-if="luanch.success"
            :title="luanch.name"
            :upcoming="luanch.upcoming"
            :success="luanch.success"
            :time="luanch.date_utc"
            :crew="luanch.crew.length"
          >
          </Card>
        </div>
      </b-tab-item>
      <b-tab-item label="Upcoming">
        <div v-for="luanch in launches" :key="luanch.id">
          <Card
            v-if="luanch.upcoming"
            :title="luanch.name"
            :upcoming="luanch.upcoming"
            :success="luanch.success"
            :time="luanch.date_utc"
            :crew="luanch.crew.length"
          >
          </Card>
        </div>
      </b-tab-item>
    </b-tabs>
  </section>
</template>

<script>
import Card from '~/components/Card'
export default {
  name: 'HomePage',
  components: {
    Card,
  },
  data() {
    return {
      isLoading: false,
      launches: [],
    }
  },
  mounted() {
    this.getData()
  },
  methods: {
    async getData() {
      const res = await this.$axios.get(
        'https://api.spacexdata.com/v4/launches'
      )
      if (res) {
        this.launches = res.data
      }
      this.isLoading = true
    },
  },
}
</script>
